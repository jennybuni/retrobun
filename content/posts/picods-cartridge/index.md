---
title: "DSpico Cartridge: A Collector's First Look"
date: 2026-09-19
author: "Retrobun"
draft: true
description: "A preliminary look at the DSpico cartridge, including what collectors should know about its features, setup, compatibility, and place in a Nintendo DS collection."
tags: ["Nintendo DS", "DSpico", "cartridge", "collecting", "hardware"]
readingTime: true
---

## A New Cartridge for the DS

There is something satisfying about clicking a cartridge into a Nintendo DS. The hardware may be getting older, but new projects continue to give collectors and players fresh ways to enjoy it. The DSpico cartridge is one of those projects, and this first look will explore what it offers, how it works, and whether it deserves a place alongside original DS releases.

> **Editor's note:** This is a preliminary draft. Product specifications, compatibility details, pricing, and hands-on observations will be added after they have been confirmed.

## What Is the DSpico Cartridge?

The project appears to be properly styled as **DSpico**, not picoDS. It is an open-source Nintendo DS and DSi flashcart project by the LNH Team, a group focused on documenting and preserving Nintendo DS-era hardware and software. The [official project page](https://www.lnh-team.org/) describes DSpico as an open-source DS(i) flashcart, with open PCB files, shell files, stickers, box art, firmware, and launcher software available for study, modification, or self-build use.

Its main purpose is not to behave like a new retail Nintendo DS release. It is a modern, RP2040-based flashcart platform for running compatible Nintendo DS and DSi software from a microSD card, experimenting with DS cartridge-bus hardware, and supporting homebrew and preservation workflows. The [firmware repository](https://github.com/LNH-team/dspico-firmware) says DSpico emulates a DS cartridge, exposes SD-card access to the DS side, exposes USB-related commands, can emulate an R4 for software such as Wood R4, and supports separate ROMs for DS and DSi/3DS systems.

## What Comes with It?

Because DSpico is an open-source project rather than a single official boxed retail product, the contents depend on whether you build one yourself or buy an assembled third-party unit.

The cartridge being used for this review was purchased from Amazon as an assembled, ready-made unit. Because DSpico is an open-source design, an Amazon listing should be treated as a third-party build unless the seller states and documents a direct connection with the LNH Team. The exact seller, purchase price, packaging, and included accessories can be added here once they have been confirmed from the order details and photographed.

The official hardware repository provides the design files for the PCB, shell, cartridge sticker, and box art. The documented hardware feature set includes an RP2040 microcontroller, 16 Mbit / 2 MB flash memory, a microSD slot, a Micro-USB port, a development port, two LEDs, and dual power support so the board can be powered from USB and the DS at the same time through an ORing circuit.

For a self-built unit, the "package" is effectively whatever the builder manufactures or sources: the PCB, components, shell, optional sticker, optional printed box art, and a separately supplied microSD card. The official guide also assumes access to a computer for compiling or preparing firmware and software.

For assembled units sold by third parties, listings may include only the cartridge. At least one current retail listing checked on 19 September 2026 lists the DSpico flashcard only and says a microSD card is not included. Any review should therefore photograph the exact purchased unit, because shell color, packaging, included storage, and cable contents may vary by seller.

Image note: the official hardware repository includes photographs and artwork for the PCB, shell, stickers, and box art, but this draft should use original photos of the review sample before publication.

Collectors will want to know how the cartridge feels in hand, whether the shell and label are well made, and how neatly it fits into a DS cartridge slot. Packaging may also matter to anyone planning to display it rather than keep it in a loose-cartridge case.

## Setup and Compatibility

The official setup path is technical, especially if building from source. The [DSpico guide](https://github.com/LNH-team/dspico/blob/develop/GUIDE.md) starts by preparing a Linux or WSL environment, installing BlocksDS, .NET 9.0, and build tools, then compiling the DLDI driver, bootloader, firmware, Pico Loader, and Pico Launcher. It then prepares the microSD card with the launcher, loader files, application lists, save lists, and any compatible DS software the user is legally entitled to use.

For an already-flashed cartridge, the practical setup should begin later in the official guide:

1. Format the microSD card using the recommended SD-card setup process.
2. Copy the `_pico` folder from Pico Launcher to the root of the microSD card.
3. Copy `LAUNCHER.nds` to the root of the card as `_picoboot.nds`.
4. Copy `picoLoader7.bin`, the DSpico build of `picoLoader9.bin`, `aplist.bin`, and `savelist.bin` into `/_pico/`.
5. Add compatible homebrew or legally owned software backups to the card.
6. Insert the microSD card into DSpico, insert DSpico into a DS, DSi, or 3DS-family system, power on the console, launch the cartridge if needed, and use Pico Launcher to browse and start software.

Questions to confirm during testing include:

- Which Nintendo DS family systems are supported? Official materials describe compatibility with DS, DSi, and 3DS-family consoles in DS/DSi modes, but individual behavior may depend on firmware, launcher setup, and exploit configuration.
- Does setup require a computer, memory card, firmware, or additional hardware? Yes: at minimum, a microSD card and prepared software files are needed. Firmware building/flashing requires a computer; already-flashed units may only require microSD preparation.
- Which file systems and storage capacities are supported? The guide points users to standard SD-card preparation instructions. R4-emulation mode has an important limitation: the firmware readme says R4 card commands cannot address SD sectors above 4 GB, so R4 software requires a card of at most 4 GB or a single partition in the first 4 GB.
- Is the cartridge region-free? DS flashcarts generally operate outside normal retail region assumptions, but this should be tested per console and software type before making a firm claim.
- Are firmware updates available, and how are they installed? Yes. The firmware readme describes easy updating: booting with the SD card ejected reboots into BOOTSEL, and the guide says the firmware `.uf2` file is copied to the USB drive that appears when DSpico is connected to a computer.
- Does sleep mode work reliably when the console is closed? Not yet tested for this review.
- Are saving, loading, and real-time clock features supported? Pico Loader uses `savelist.bin` and supports retail DS(i) ROM loading, but save reliability, save type coverage, and RTC behavior need hands-on testing with specific titles.

Photos to add before publication: the prepared microSD contents on a computer, the cartridge inserted in each tested console, the DS menu showing the cartridge, Pico Launcher running, and at least one homebrew title running on original hardware.

## Using It on Original Hardware

Hands-on testing is still needed before this section can become a verdict. Based on the official software descriptions, the intended everyday flow is straightforward: boot the console, open the DSpico cartridge entry if the system does not autoboot it, browse files in [Pico Launcher](https://github.com/LNH-team/pico-launcher), and launch software through [Pico Loader](https://github.com/LNH-team/pico-loader). Pico Launcher supports multiple browsing styles, themes, custom covers, file associations, background music, and cheats, while Pico Loader supports homebrew and retail DS(i) ROM loading across several flashcart platforms, including DSpico.

The key things to verify on original hardware are startup speed, whether Pico Launcher consistently appears, how quickly files are listed, whether repeated launch attempts behave consistently, and whether saves survive multiple power cycles. Pico Loader's documentation notes that return-to-loader is not currently supported in retail games, so readers should expect to power cycle or reset through normal console behavior rather than jump straight back to the menu from every title.

Compatibility should be treated carefully. The DSpico firmware is capable, but this is still an enthusiast project with several moving parts: firmware, bootloader, launcher, loader, microSD card formatting, and the software being launched. A final review should include a tested list rather than a broad "everything works" statement.

A useful hands-on test would include several types of software, repeated save-and-load checks, sleep mode, and use across every supported DS model available for testing.

## Build Quality

The official design is unusually transparent for a flashcart project. The [hardware repository](https://github.com/LNH-team/dspico-hardware) includes the PCB design, fabrication files, shell CAD files, cartridge sticker artwork, and box-art artwork. That makes DSpico interesting from a collector and hardware-preservation perspective even before considering day-to-day use: the object is documented, reproducible, and modifiable rather than locked behind an anonymous shell.

Officially documented board features include the RP2040 microcontroller, 16 Mbit flash memory, Micro-USB port, microSD slot, development port, red and blue LEDs, and dual power support. The development port exposes UART, I2C, two GPIO lines, SWD debug, and 3.3 V power up to 50 mA, which reinforces that DSpico is also a hardware experimentation platform.

This draft should not claim final fit-and-finish quality until the review unit is inspected. The points to check are the shell seam, sticker alignment, contact cleanliness, whether the cartridge inserts smoothly, whether the microSD slot is easy to access, whether the Micro-USB port feels secure, and whether the LEDs are visible without being distracting.

Unlike an original retail game, a modern cartridge should not be judged by whether it copies Nintendo's labels or molding. More useful questions are whether it is clearly identified, built consistently, easy to insert and remove, and unlikely to place unnecessary strain on aging hardware.

## Where It Fits in a Collection

The DSpico cartridge is not a replacement for an original boxed game. Original releases still carry their own history, artwork, manuals, and memories. A modern cartridge may instead be a practical companion: something to use for experimentation or regular play while collectible copies remain safely stored.

Its strongest collector-facing use cases are likely homebrew exploration, hardware experimentation, testing legally made backups without repeatedly handling valuable cartridges, and learning how modern open-source flashcart projects are built. It may also appeal to people who enjoy preservation-adjacent hardware: not only using a cartridge, but being able to inspect the PCB, shell, firmware, loader, and launcher sources.

It may not be ideal for someone who wants a polished commercial product with a fixed accessory bundle, official retail support, or guaranteed compatibility across a personal library. It is also not the right fit for readers who only want original Nintendo-published cartridges on their shelf. DSpico sits better beside tools, adapters, flashcarts, and homebrew devices than beside boxed retail games.

## Price and Availability

Checked on 19 September 2026: the LNH Team does not appear to sell DSpico as an official commercial product. In fact, the hardware repository includes a statement saying the LNH Team has no affiliation with commercial projects and does not endorse for-profit DSpico projects or related materials. The official availability is therefore the open-source project itself: hardware files, shell files, artwork, firmware, launcher, loader, and documentation.

Assembled cartridges are available from third-party sellers, but those should be described as third-party assembled units rather than official LNH Team stock. One third-party listing checked on 19 September 2026, [Romkids in Germany](https://www.romkids.de/bwlm-shop/konsolen-videogames/nintendo/nintendo-game-boy/speicherkarten-game-boy/dspico-flashcard-nintendo-ds-dsi/), lists a "DSpico Lite v2.1 Flashcard" for 16.79 EUR including VAT, before shipping, with stock shown as available. That listing says the package includes one DSpico flashcard and does not list a microSD card.

The review unit was bought through Amazon, which shows that assembled DSpico cartridges are also available through larger online marketplaces. Amazon listings and sellers can change, so the final review should record the seller name, price paid, purchase date, delivery region, and exactly what arrived rather than treating one listing as a permanent source or an official store.

Before buying, readers should confirm that they are looking at the official product and understand exactly what is included. If similar-looking cartridges exist, this section should explain how to identify the genuine project without presenting unofficial copies as authentic.

## Things to Consider Before Buying

- Check the official documentation and issue trackers for your console, intended software, and firmware version.
- Read the project's documentation before ordering any additional storage or accessories.
- Confirm whether future firmware updates are expected.
- Prefer the official project documentation, and treat assembled retail units as third-party builds unless the seller can show a direct relationship with the project.
- Keep backups of important save data where the cartridge supports them.
- Use homebrew and backup features responsibly, and only with software you are legally entitled to use.

## Early Verdict

On paper, DSpico's best feature is its openness. The PCB, shell, artwork, firmware, loader, and launcher are documented in a way that makes the cartridge more than another anonymous DS flashcart. Its greatest limitation for a typical collector is the same thing: this is an enthusiast project, and the experience depends on firmware, SD-card setup, third-party assembly quality, and software compatibility.

The ideal user is a DS enthusiast who is comfortable reading documentation, preparing a microSD card, and treating the cartridge as a preservation and experimentation tool. The less ideal user is someone who wants a plug-and-play retail-style product with a single official box, seller, warranty, and compatibility promise.

The most interesting thing about projects like DSpico is that they keep people engaged with original hardware. If it proves reliable and approachable in hands-on testing, it could become a useful tool for DS enthusiasts without taking anything away from the pleasure of collecting original games.

## Sources Checked

- [LNH Team DSpico project page](https://www.lnh-team.org/)
- [DSpico hardware page](https://www.lnh-team.org/dspico_hw.html)
- [DSpico project index on GitHub](https://github.com/LNH-team/dspico)
- [DSpico setup guide](https://github.com/LNH-team/dspico/blob/develop/GUIDE.md)
- [DSpico firmware repository](https://github.com/LNH-team/dspico-firmware)
- [DSpico hardware repository](https://github.com/LNH-team/dspico-hardware)
- [Pico Loader repository](https://github.com/LNH-team/pico-loader)
- [Pico Launcher repository](https://github.com/LNH-team/pico-launcher)
- [Romkids DSpico Lite v2.1 listing](https://www.romkids.de/bwlm-shop/konsolen-videogames/nintendo/nintendo-game-boy/speicherkarten-game-boy/dspico-flashcard-nintendo-ds-dsi/)
