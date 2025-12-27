# Hyperdrive II Recovery Notes

## Overview

These notes describe how Hyperdrive II was recovered and why this repository
exists. The focus here is narrative: the technical details live in the broader
Microbee preservation work and in the companion Caverns project.

## Background

Hyperdrive II is a science-fiction text adventure for the Microbee, written by
John Hardy. It was based on a story by Ken Stone and an earlier VIC-20 version
of the game, but it was reworked into a new title using the BASIC engine that
powered Caverns. The result is a distinct game, not a port of Ken's Hyperdrive.


## Copyright and Copy Protection

The protected listing carries a clear copyright marker. In the protected
release, the title screen prints "by John Hardy (1983)," which is a useful
historical signal: Australian copyright law did not explicitly list computer
programs as protected works until the 1984 amendments introduced under the
Hawke/Keating government's first term. That makes the 1983 notice a small but
interesting marker of intent, written just before the law caught up with the
medium.

The protected version also includes a deliberate anti-listing routine aimed at
casual copying. The game was intended to autorun from tape; under normal
conditions, a user could interrupt the run and type LIST to print the code.
To prevent that, the startup code POKEs a small machine-code stub into spare
RAM (see line 100 in `src/protected/hyperdrive2.basic` and the corresponding
assembly in `src/protected/obfuscation.asm`). When the break key or error trap
fires, that stub overwrites the BASIC program area and then forces a warm reset,
leaving nothing to list. It is a lightweight protection scheme, but typical of
the period and effective against casual inspection.

## Discovery and Recovery

The Microbee version of Caverns was distributed on cassette. Hyperdrive II was
found on the B side of one such cassette that otherwise contained Caverns for
the 16K Microbee. The tape survived in hobbyist collections and was preserved
through the Microbee Software Preservation Project.

Alan Laughton (aka ChickenMan) played a critical role in compiling preservation
media and helping recover the original program text. His guidance and generosity
made it possible to reconstruct the listing and restore the game to readable
form.

## Correspondence Notes (2019 to 2021)

Email exchanges from the recovery period add useful context:

- In late 2010, Caverns and Hyperdrive II were compiled onto a "Games 5" disk
  as part of a bootable menu collection assembled for Microbee users.
- In February 2019, Alan confirmed that the preserved copies were not extracted
  from original Dreamcards disks, and shared the tokenized MWB files so the
  listings could be recovered.
- He also described a practical workflow: load the WAV into a Microbee (or the
  ubee512 emulator), then save the MWB using the debugger and memory range from
  the monitor.
- Alan provided a link to a MWB-to-text utility and confirmed that DAT2WAV had
  been used to make WAV files for members using ROM Microbees.
- In April 2021, a friend recorded the Dreamcards DUO 3 tape, revealing the
  intro programs for Caverns and Hyperdrive II and a scan of the tape insert.
  ASCII listings of those intro programs were shared shortly after.

Those notes explain why the repository includes separate intro listings and
why the project is tied to the DUO era rather than to the VIC-20 release.

## What Was Preserved

The recovery aims to keep the program intact, not to reinterpret it. The core
goal is to preserve:

- the original listing
- the recovered program data
- the context of where the tape came from

As artifacts are added to this repository, they will live under `src/`.

## Acknowledgements

Thanks to the Microbee Software Preservation Project and especially to Alan
Laughton for preserving the tape collections and helping recover the original
text of Hyperdrive II.
