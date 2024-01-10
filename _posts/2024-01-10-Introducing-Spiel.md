---
title: 'Introducing Spiel'
author: Eitan
layout: post
permalink: /2024/01/10/Introducing-Spiel/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Software
  - Technology
---

## A New Speech API and Framework

<img src="/assets/uploads/2024/01/spiel-logo.svg" alt="Spiel Logo" style="max-width: 30vw; float: right; margin-left: 1rem;">

I wrote the beginning of what I hope will be an [appealing speech API for desktop Linux and beyond](https://github.com/eeejay/libspiel). It consists of two parts, a [speech provider interface specification](https://eeejay.github.io/libspiel/generated-org.freedesktop.Speech.Provider.html) and a [client library](https://eeejay.github.io/libspiel/). My hope is that the simplicity of the design and its leverage of existing free desktop technologies will make adoption of this API easy.

Of course, Linux already has a speech framework in the form of [Speech Dispatcher](https://github.com/brailcom/speechd). I believe there have been a handful of technologies and recent developments in the free desktop space that offer a unique opportunity to build something truly special. They include:

### D-Bus
D-Bus came about several years after Speech Dispatcher. It is worth pausing and thinking about the different architectural similarities between a local speech service and a desktop IPC bus. The problems that Speech Dispatcher tackles, such as auto-spawning, wire protocols, IPC transports, session persistence, modularity, and others have been generalized by D-Bus.

Instead of a specialized module for Speech Dispatcher, what if speech engines just exposed an interface on the session bus? With a service file they can automatically spawn and go away as needed.

### Flatpak (and Snap??)
Flatpak offers a standardized packaging format that can encapsulate complex setups into a sandboxed installation with little to no thoughts of the [dependency hell](https://en.wikipedia.org/wiki/Dependency_hell) Linux users have grown accustomed to. One neat feature in Flatpaks is that they support exposing fully sandboxed D-Bus services, such as a speech engine. Flatpaks offer an out-of-band distribution model that sidesteps the limitations and fragmentation of traditional distro package streams. Flatpak repositories like [Flathub](https://flathub.org) are the perfect vehicle for speech engines because of the mix of proprietary and peculiar licenses that are often associated with them, for example…

### Neural text to speech
I have always been frustrated with the lack of naturally sounding speech synthesis in free software. It always seemed that the game was rigged and only the big tech platforms would be able to afford to distribute nice sounding voices. This is all quickly changing with a flurry of [new](https://github.com/rhasspy/piper/tree/master "Piper") [speech](https://github.com/MycroftAI/mimic3/tree/master "Mimic3") [systems](https://github.com/coqui-ai/TTS "Coqui TTS") covering many languages. It is very exciting to see this happening, it seems like there is a new innovation on this front every day. Because of the size of some of the speech models, and because of the eclectic copyright associated with them we can’t expect distros to preinstall them, Flatpaks and Neural speech systems are a perfect match for this purpose.

### Talking apps that aren’t screen readers
In recent years we have seen many new applications of speech synthesis entering the mainstream - navigation apps, e-book readers, personal assistants and smart speakers. When Speech Dispatcher was first designed, its primary audience was blind Linux users. As the use cases have ballooned so has the demand for a more generalized framework that will cater to a diverse set of users.

There is [precedent for technology that was designed for disabled people becoming mainstream](https://ssir.org/articles/entry/the_curb_cut_effect). Everyone benefits when a niche technology becomes conventional, especially those who depend on it most.

## Questions and Answers
I’m sure you have questions, I have some answers. So now we will play our two roles, you the perplexed skeptic, unsure about why another software stack is needed, and me - a benevolent guide who can anticipate your questions.

### Why are you starting from scratch? Can’t you improve Speech Dispatcher?
Speech Dispatcher is over 20 years old. Of course, that isn’t a reason to replace it. After all, some of your [favorite](https://www.vim.org/) [apps](https://www.mozilla.org/) are even older. Perhaps there is room for incremental improvements in Speech Dispatcher. But, as I wrote above, I believe there are several developments in recent years that offer an opportunity for a clean slate.

### I love eSpeak, what is all this talk about “naturally sounding” voices?
eSpeak isn’t going anywhere. It has a permissible license, is very responsive, and is ergonomic for screen reader users who [consume speech at high rates](https://www.youtube.com/watch?v=DFkmRewclaE) for long periods of time. We will have an eSpeak speech provider in this new framework.

Many other users, who rely on speech for narration or virtual assistants will prefer a more natural voice. The goal is to make those speech engines available and easy to install.

### I know for a fact that you can use /insert speech engine/ with Speech Dispatcher
It is true that with enough effort you can plug anything into Speech Dispatcher.

Speech Dispatcher depends on a fraught set of configuration files, scripts, executables and shared libraries. A user who wants to use a synthesis engine other than the default bundled one in their distro needs to open a terminal, carefully place resources in the right place and edit configuration files.

### What plan do you have to migrate all the current applications that rely on Speech Dispatcher?
I don’t. Both APIs can coexist. I’m not a contributor or maintainer of Speech Dispatcher. There might always be a need for the unique features in Speech Dispatcher, and it might have another 20 years of service ahead.

### I couldn’t help but notice you chose to write libspiel in C instead of a modern memory safe language with a strong ownership model like Rust.
Yes.