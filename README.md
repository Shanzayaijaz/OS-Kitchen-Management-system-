# OS-Kitchen-Ordering-system-

This project simulates a kitchen environment where multiple chefs work concurrently using shared kitchen resources. It uses POSIX threads (pthread) and semaphores to manage resource access and maintenance, simulating a real-world kitchen with equipment usage, cleaning, and failures.

## Features

- Shared Kitchen Resources: Stove, Knife, Chopping Board, Vegetables, and Cooking Pot.
- 10 Chefs: Each chef has unique resource needs and skill levels.
- Timed Resource Acquisition: Prevents deadlocks by timeout handling.
- Dynamic Resource States:
  - Available
  - In Use
  - Needs Cleaning
  - Under Maintenance (Broken)
- Cleaning and Maintenance: Automatically handled by a dedicated kitchen manager thread.
- Status Reporter: Periodically logs resource states, usage, and quality.
- Color-coded Terminal Output: For better readability.

## Threads

- Chef Threads: Try to acquire needed resources, cook meals, and release them.
- Kitchen Manager Thread: Checks and maintains resources periodically.
- Reporter Thread: Prints status reports of all kitchen resources.

## How It Works

1. Each chef needs 2 resources to cook.
2. Resources degrade with use. After multiple uses, their quality drops.
3. When quality hits 0, the resource becomes broken and needs maintenance.
4. Cleaning and maintenance restore resource availability and quality.
5. Chefs wait or retry based on resource availability.

## Build Instructions

Make sure you have a C compiler and POSIX threads support (Linux/Unix environment recommended).

```bash
gcc -o kitchen_simulation main.c kitchen.c -lpthread
./kitchen_simulation
