# MinecraftD
A small toolset to register minecraft servers as systemd services.

*HINT* This works with minimal modification for every server software without provided deamonizing.

## The problem
Out of the box, a minecraft server is directly started as a JAR. It will present you with a CLI and promt log messages. Deamonizing could be done by tools like NoHup or Screen. Dig into it and you'll find that both of them have their drawbacks.<br>

## The solution
This toolset works by forking the server executable and providing a FIFO to write to stdin. Stdout is written to a regular file.<br>
Also provided is a CLI script which tails the output file and redirects its stdin to the FIFO (linewise). In that way, you can safely CTRL+C out of the CLI without killing your server and won't have to worry about how to get out of exit your screen process correctly.
