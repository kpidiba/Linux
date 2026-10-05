If you're on **Pop!_OS/Linux** and your Bluetooth mouse **moves the cursor but clicking doesn't work**, the Bluetooth connection itself is probably fine. The problem is usually one of these:

1. **Mouse button mapping is wrong**
2. **Bluetooth HID input issue**
3. **Mouse is connected but not fully recognized**
4. **Another input device/software is interfering**
5. **The mouse itself has a hardware/button problem**

Let's identify which one it is.

### First, try this simple test

Open a terminal with `Ctrl + Alt + T` and run:

```
xev
```

A small white window will appear.

Move the mouse over that window and **left-click**.

You should see something like:

```
ButtonPress eventbutton 1
```

Then release:

```
ButtonRelease eventbutton 1
```

### What the result means

- **You see `ButtonPress` / `ButtonRelease`** → Linux receives the click, so it's likely a desktop/configuration problem.
- **You see nothing when clicking** → the Bluetooth mouse isn't sending button events correctly, so we'll investigate Bluetooth/HID.
- **Right-click works but left-click doesn't** → likely button mapping or a physical left-button issue.
- **Mouse doesn't even move** → Bluetooth connection problem rather than a click problem.

Tell me **what happens with `xev` when you click**, and I can give you the exact fix.
