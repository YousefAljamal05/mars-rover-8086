# mars-rover-8086

This project is a 2D grid simulation developed in 8086 Assembly Language for the Microprocessors course at Princess Sumaya University for Technology. It features an autonomous "Mars Rover" that navigates an 8x8 terrain based on a sequence of commands issued by "Mission Control".

## Project Overview

The objective is to guide the Rover through a personalized terrain filled with obstacles (craters). The program handles 2D array memory addressing, movement logic, and step-by-step animation using BIOS interrupts.

### Key Features

* **Unique Map Generation**: Exactly 6 obstacles are placed based on modulo arithmetic applied to student IDs.
* **Command Processing**: Supports a case-insensitive string of movement commands (U, D, L, R) up to 20 characters.
* **Boundary Detection**: If the Rover moves off the 8x8 edge, the simulation halts with a "Boundary breach!" error.
* **Collision Detection**: If the Rover hits a crater, a warning beep sounds and the mission is aborted.
* **Fuel System**: The Rover starts with a 20-unit fuel battery, deducting 1 unit per successful move.
* **Visual Animation**: The grid updates with a small delay loop so the user can watch the Rover move step-by-step.
* **Bonus Feature - Fuel Tanks**: The grid includes fuel tanks. When the Rover navigates to a fuel tank, 5 units are added to the fuel battery.
* **Bonus Feature - Path Tracing**: As the Rover navigates the grid, it leaves behind a visual trace to keep track of its movement history.

## Technical Specifications

### Map Logic & Obstacle Placement

The 8x8 grid is a 2D array in memory. Obstacles are calculated using the following modulo arithmetic for each student ID (d1 d2 d3 d4 d5 d6 d7 d8):

* Obstacle 1: Row = d7 mod 8, Col = d8 mod 8
* Obstacle 2: Row = d5 mod 8, Col = d6 mod 8
* Obstacle 3: Row = d3 mod 8, Col = d4 mod 8 (if needed)

Note: The Rover always starts at coordinate (0,0). If an obstacle coordinate lands exactly on (0,0), it is manually shifted to (0,1).

### Grid Legend

The system uses the following ASCII characters for the display:
* . : Empty Space
* O : Craters (Obstacles)
* R : Rover (Starting at 0,0)
* F : Fuel Tank (+5 Fuel Units)
* * : Rover Path Trace

## Execution Outcomes

* **Mission Success**: The sequence completes successfully, displaying the remaining fuel.
* **Boundary Breach**: The Rover attempts to move outside the 8x8 edge; simulation halts.
* **Critical Failure**: The Rover hits an obstacle; simulation halts with a crash message.

## How to Run

1. Open the .asm file in emu8086.
2. Emulate and run the program.
3. Observe the generated map based on the provided IDs.
4. Enter a movement sequence when prompted.
