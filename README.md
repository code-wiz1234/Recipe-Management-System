# Recipe-Management-System


This project provides a graphical user interface for creating, storing, and retrieving machining recipes on FANUC Series 0i CNC controllers. Each recipe contains 10 configurable parameters stored in CNC macro variables.

## Features

- Create Recipes: Input and define up to 10 different recipes (numbered 1-10)
- Parameter Storage: Each recipe stores 10 parameters in dedicated macro variable ranges
- Retrieve Recipes: Load previously saved recipes into the active macro variable range (600-609)
- Graphical Interface: 640x480 VGA display with soft-key navigation

## How It Works

## Recipe Storage Mapping
| Recipe # | Macro Variables |
|----------|-----------------|
| 1        | 500 - 509       |
| 2        | 510 - 519       |
| 3        | 520 - 529       |
| ...      | ...             |
| 10       | 590 - 599       |

When retrieved, any recipe's parameters are copied to variables 600-609 for active use.

### User Interface
The system uses FANUC's soft-key interface:
- F0 (Create): Enter a new recipe number and define 10 parameters
- F1 (Save): Store the current parameters to the appropriate macro variable range
- F2(Retrieve): Load a saved recipe into the active range (600-609)

## Technical Details

### Built With
- C Language Executor - FANUC's embedded C development environment
- FANUC Libraries - CNC data access functions
- MS-C Graphics - 640x480 VGA display functions

### Key Functions Used
| Function | Purpose |
|----------|---------|
| `cnc_wrmacro()` | Write values to CNC macro variables |
| `cnc_rdmacro()` | Read values from CNC macro variables |
| `crt_opengr()` | Initialize graphics display |
| `_setvideomode()` | Set VGA video mode (640x480, 16 colors) |
| `_rectangle()` | Draw UI elements |

### CNC Architecture Overview
```
┌─────────┐    Optical    ┌─────────┐         ┌─────────┐
│   CNC   │◄──  Fiber  ──►│  Drive  │◄───────►│  Motor  │
│ (GCode) │    Cable      │ (AC/DC) │         │(Encoder)│
└────┬────┘               └─────────┘         └────┬────┘
     │                                              │
     │              Feedback Loop                   │
     └──────────────────────────────────────────────┘
```



## Building & Deployment

1. Compile using FANUC's NMAKE toolchain
2. Generate memory card file (*.mem)
3. Load onto CNC during boot sequence


## What I Learned

- Embedded C programming for industrial controllers
- CNC macro variable manipulation
- PMC (Programmable Machine Control) concepts
- Bit manipulation for hardware register access
- Graphics programming in resource-constrained environments



*Developed during Summer Internship at FANUC India, July 2024*
