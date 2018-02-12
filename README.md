# wsl-beep
Beep for WSL Ubuntu and other Linux distros in Windows 10 e.g. Cygwin. The built-in [`beep`](https://linux.die.net/man/1/beep) in 
Ubuntu doesn't work in WSL (Windows Subsystem for Linux), but I've modified it to use
[Windows Beep()](https://msdn.microsoft.com/en-us/library/windows/desktop/ms679277(v=vs.85).aspx)
e.g. `powershell.exe "[console]::beep(261.6,700)"`. In a WSL Linux the frequency must be between 37.0 and 32767.0 Hz,
but it pauses if the frequency is less than 37.0. The original beep supported floating point frequences,
but in Windows they are probably truncated to integers.

Build and install in Ubuntu using:
```
make
sudo make install
beep -f 261.6 -l 700
```
In Cygwin you have to modify the Makefile.

This makes it possible to play the files in https://github.com/ShaneMcC/beeps or the command-lines in https://www.reddit.com/r/linux/comments/18h8v5/does_anyone_have_or_know_a_source_for_beep_scripts/.

You can break out of the playing files by pressing Ctrl+C for a long time.

Now I use `system()`, but one might use a more direct call with less overhead, but I don't know how. Another alternative would
be to write a TCP/IP sound server.
