## Purpose

This C# console program is essentially an auto-clicker designed to repeatedly click line by line inside the currently active (foreground) application window (like Visual Studio editor). It moves the mouse down one line at a time and clicks, with a configurable interval.

## Key Parts

#### 1. Win32 API Imports

GetForegroundWindow() → gets the handle of the currently active window.

GetWindowRect() → retrieves the window’s screen coordinates (left, top, right, bottom).

mouse_event() → simulates mouse clicks.

#### 2. Constants

MOUSEEVENTF_LEFTDOWN / MOUSEEVENTF_LEFTUP → define mouse left button click actions.

#### 3. RECT struct

Stores the window boundary (Left, Top, Right, Bottom).

#### 4. Main Logic

Waits 5 seconds at startup (Thread.Sleep(5000)).

Captures the current mouse start position (startX, startY).

Defines:

intervalMs = 60000 → 1 minute delay between clicks.

lineHeight = 18 → how much to move down each click (approx. one line in an editor).

Loops infinitely:

Gets the active window’s handle & dimensions.

Checks if the cursor has reached the bottom → resets back to the starting Y position.

Moves the cursor to (startX, currentY).

Simulates a left mouse click at that position.

Increments currentY by lineHeight (moves down one line).

Sleeps for 60 seconds before repeating.

#### 5. Exit Handling

Console.CancelKeyPress ensures the app exits cleanly when pressing Ctrl+C.

### In Simple Words

This program:

Waits 5 seconds after launch.

Then every 60 seconds:

Moves the mouse down one “line” at a time (18 pixels).

Clicks at that position.

Resets to the starting position once it reaches the bottom of the window.

So it behaves like a robot that clicks through lines in an editor window at regular intervals.
