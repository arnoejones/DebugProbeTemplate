# DebugProbeTemplate
This is the basic template to setup a Debug Probe on MacOS (I happen to be on Catalina right now) with VSCode and the Pi Pico SDK.

I learned what I needed to know to make this work by Embedded at Plymouth - https://www.youtube.com/watch?v=T09zMnDtpZ4

I spent some time trying to make Pico Probe work until I discovered that Pico Probe and Debug Probe (the actual dedicated hardware bit) are two different things.  I also discovered that there is a sample launch.json in Pico-Examples/ide/vscode.  

1st, I created this project by launching ./pico-project-generator/pico_project.py --gui

In the gui I selected my already-made directory and gave it a name.
  For fun I checked off a couple of Library Options but I didn't need to.
  I checked Console over UART in Console Options
  I checked Create VSCode and Pico Probe from the drop down.  Interestingly enough, the second example I tried included CMSISDAP Debug Probe!
  Then I clicked OK.

Next, I copied  launch-remote-openocd.json from pico-examples/ide/vscode/ to the .vscode directory in my project.
In my case I changed "gdbPath" to "gdbPath" : "arm-none-eabi-gdb", instead of "gdb Multiarch"
I modified "gdbTarget" to "localhost:3333"

 From there I did a Debug build and launched the project and saw that I have full debug capabilities!
