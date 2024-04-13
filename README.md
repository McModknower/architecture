# Untitled Architecture

This repository contains the description of a custom untitled computer architecture for the game [Turing Complete](https://store.steampowered.com/app/1444480/Turing_Complete/).

This architecture was made just for fun, and is implemented as described here in a save file on my pc. If you want to know anything about it that is not described here, join the turing complete discord and ping me in #computer-architecture, or open an issue.

This is an 8-bit, risc, save-load, fixed with, 4 octet instruction architecture with a focus on easy implementation in the game.

## Parts

- [Instructions & Instruction Layout](instructions.md) describes how instructions are structured and what opcodes are available.
- [The bus](bus.md) is the place where data and signals are transferred between components.
- [Registers](registers.md) describes what registers are (or should) be used for what purpouse.
- [The ALU](alu.md) calculates arithmetic and logic operations.
- [RAM](ram.md) is also present to store more data.
- [IO Ports](io.md) for solving levels acessible too.
- TODO: add rest
