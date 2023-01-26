# Z CAM C1: Unofficial Docs
https://github.com/acceptableEngineering/Z-CAM-C1-Unofficial-Docs

----

### What is the C1?
The C1 was a camera released by Chinese cinema camera maker Z CAM, in collaboration with Chinese company ImagineVision. It's very difficult to find information about this camera, as it was not long-lived. Imagine a powerful, industrial GoPro that can be commanded via wired network. A nice Sony sensor plus Micro Four-Thirds (MFT) lens mount results in a very versatile, tough camera.

### Why do we care?
You can pick these up used for ~$200 after tax online. In my case, this is the perfect camera for multi-camera streaming, and they cost less than low-end Sony Handycams. It runs an HTTP API, and runs Linux with SSH.

### So what is this git repo?
There is zero official documentation on this API-driven camera. "Kyle" on the [Frame Voyager Discord](https://discord.gg/4JGqNNPsJ2)'s #z-cam channel originally told me about this camera body and has been nice enough to share some tips, tricks, and other info. I've made my own discoveries too, so hoarding all of this information in one place that facilitates collaboration seemed like the next move.

----

## Disclaimer
I'm just a guy getting to know these cameras better for use with my own web application. You can brick your C1 if you're not careful with SSH and API requests, so be careful. I can't be held responsible for any damage you cause to your C1.

----

## Discoveries

### Linux, Telnet, SSH
You can SSH into these cameras, found by:
```
$ nmap 192.168.1.98 | grep open
23/tcp   open  telnet <-- Telnet facilitating SSH
80/tcp   open  http <-- C1's API Server
9876/tcp open  sd <-- Video Streaming Server
9999/tcp open  abyss <-- Unsure what this is
```

Telnet facilitates the SSH session:
```
telnet 192.168.1.98
Trying 192.168.1.98...
Connected to 192.168.1.98.
Escape character is '^]'.

a9 login: root
```

### On-Screen Menu
We haven't figured out how to navigate the on-screen menu on the version of the C1 without the build-in display, but I found that you can do the following to launch it:
- Unplug power
- Plug power back in
- Press and release the Power button
- Hold down the Record and Power buttons until the C1 turns on
- You should now see a menu like this

![Screenshot](https://github.com/acceptableEngineering/Z-CAM-C1-Unofficial-Docs/raw/master/.github/readme-images/on-screen-menu.png)
