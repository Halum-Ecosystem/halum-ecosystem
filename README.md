# Halum

Halum is an online community dedicated to the progress of biomedical technology through collaboration and low-cost innovation. It helps bridge the gap between STEM fields and beyond, to create projects that can one day be applied in the real world.

Halum is for medical students and healthcare workers, engineers, clinicians, hobbyist makers, and anyone interested in getting involved in biomedical engineering.

## Vision

A place where people share ideas, get inspired and work together on practical projects that go on to make a difference in industries around the world.

## What we do

- **Physical devices:** open, low-cost biomedical hardware that anyone can build, study and improve, starting with a prosthetic hand.
- **Systems integration:** software that connects sensors, signal processing and outputs into one system, so new devices can be plugged in without rebuilding everything.
- **Showcasing members' work:** a place to present what you are building, whether or not it is a Halum project, and get feedback from people across medicine and engineering.

## Why Halum

I'm a 6th-year medical student moving into engineering through a biomedical engineering lab at my university. Halum started as a way to share that work, and grew into the idea of a community where medicine and engineering meet to share ideas and inspiration. I don't know yet what it will lead to, but I hope it's the beginning of something great.

Every Halum project is built around three questions:

1. Can we build something that measures a biological signal?
2. Can we explain and computationally analyse what that signal represents?
3. Can we use that information to make an external system respond intelligently?

If these three are not considered, it isn't worth doing much else. Every system takes an input, does something with it, and produces an output.

## Projects

| Project | Category | What it does | Status |
|---|---|---|---|
| [halum-platform](https://github.com/Halum-Ecosystem/halum-platform) | Systems integration | Connects biomedical sensors, processing and outputs into one modular system. First goal: a simulated muscle (EMG) signal driving a virtual hand. | Planning |
| [halum-prosthetic-hand](https://github.com/Halum-Ecosystem/halum-prosthetic-hand) | Physical device | An open, low-cost prosthetic hand: designs, firmware and build guides. | Planning |

## How this repo is organised

This repository is the hub of Halum. It holds the community documents, and links to each project, which lives in its own repository:

```
halum-ecosystem/
  README.md        this page
  Safety.md        safety rules for all Halum projects
  projects/
    platform/      -> halum-platform
    hand/          -> halum-prosthetic-hand
```

The folders in `projects/` are Git submodules, which are links to a specific version of each project. To download the hub with every project included:

```
git clone --recurse-submodules https://github.com/Halum-Ecosystem/halum-ecosystem.git
```

If you already cloned without that option and the project folders are empty, run `git submodule update --init` inside the hub.

To work on a project, clone its own repository and open issues and pull requests there.

## Get involved

Halum is still in its infancy, and we are designing the first projects now, so this is the best time to help shape them.

- **Join the conversation** in [Discussions](https://github.com/Halum-Ecosystem/halum-ecosystem/discussions): introduce yourself, share ideas, or show what you are working on.
- **Report a problem or suggest a change** in the Issues of the project it concerns. Use this hub's [Issues](https://github.com/Halum-Ecosystem/halum-ecosystem/issues) for anything about Halum as a whole.
- **Contribute:** the [contributing guide](https://github.com/Halum-Ecosystem/.github/blob/main/CONTRIBUTING.md) explains how.

## Safety

Halum is for research and education only. Nothing here is a medical device. Read [Safety.md](Safety.md) before building or running any Halum project.

## Licence

Each project sets out its own licence:

- [halum-platform](https://github.com/Halum-Ecosystem/halum-platform): Apache-2.0.
- [halum-prosthetic-hand](https://github.com/Halum-Ecosystem/halum-prosthetic-hand): CERN-OHL-S-2.0 for hardware designs, Apache-2.0 for firmware and software.

The documents in this hub are licensed under CC-BY-4.0 (see [LICENSE](LICENSE)).
