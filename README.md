# Installation of Python (WS22)

In this lecture we use Python 3.10 as our programming language. This guide follows the steps for installing python 3.10 for Windows, macOS and Debian Linux. Fill out the [feedbackr](https://www.fbr.io/info) after the installation.


## Windows

Download the installer here:
* [Windows (64-bit)](https://www.python.org/ftp/python/3.10.7/python-3.10.7-amd64.exe)
* [Windows (32-bit)](https://www.python.org/ftp/python/3.10.7/python-3.10.7.exe)


1. Open the downloaded Python installer.   
**Make sure to check the &#34;Add Python 3.10 to PATH&#34; mark!**
![](https://i.imgur.com/qfydlwD.png)
&lt;!-- ![](https://i.imgur.com/KGl4G4R.png) --&gt;

2. Click on &#34;Install Now&#34;. This may take a while.
![](https://i.imgur.com/Osksm4e.png)
&lt;!-- ![](https://i.imgur.com/j4YtFCJ.png) --&gt;

3. To finish the installation, click &#34;Close&#34;.
![](https://i.imgur.com/pViS2Ix.png)


### Verify Installation
To check if you successfully installed Python open up a new Terminal. Press the Windows key&lt;kbd&gt;![](http://i.stack.imgur.com/T0oPO.png)&lt;/kbd&gt;, type `cmd` and hit enter. 

A new terminal window opens up which should look something like this:
![](https://i.imgur.com/TJl9DoU.png)

Next, enter ``python --version`` in the terminal and hit enter.
![](https://i.imgur.com/A3fHfcS.png)

You should see the currently installed version of Python.

## macOS
You can install python using **either** the installer package &lt;span style=&#34;color:red&#34;&gt;**OR**&lt;/span&gt; homebrew.
#### Using the installer package (.pkg)
Download the installer here
* [macOS 11](https://www.python.org/ftp/python/3.10.7/python-3.10.7-macos11.pkg)

1. Open the downloaded installer package, click on &#34;Continue&#34; and accept the licence
![](https://i.imgur.com/N3Jl0Xt.png)

2. Click on &#34;Install&#34;
![](https://i.imgur.com/61IlQ5m.png)


3. Finish the installation
![](https://i.imgur.com/zssbEvy.png)


#### Using homebrew
[Homebrew](https://brew.sh) is a free software package manager that can be installed by pasting the following line into the terminal (To open a terminal, press &lt;kbd&gt;&amp;#8984;&lt;/kbd&gt;+&lt;kbd&gt;Space&lt;/kbd&gt;, type `Terminal` and hit enter)

&gt;``/bin/bash -c &#34;$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)&#34;``

You might need to install Xcode command line tools first, by typing the following line into your terminal
&gt;``xcode-select --install``

You can install python 3.10 by typing
&gt;``brew update &amp;&amp; brew install python@3.10``

**Optional**: You might want to add symbolik links like python-&gt;python3 and pip-&gt;pip3 to your Path by typing


&gt; ``echo -n &#39;export PATH=/opt/homebrew/opt/python@3.10/libexec/bin:$PATH&#39; &gt;&gt; ~/.zshrc``
### Verify installation
Open a terminal (To open a terminal, press &lt;kbd&gt;&amp;#8984;&lt;/kbd&gt;+&lt;kbd&gt;Space&lt;/kbd&gt; and type `Terminal`), type `python --version` and hit enter.
![](https://i.imgur.com/OvUU05Y.png)

If an error is displayed like `command not found: python`, try `python3 --version` instead.
## Debian
If you are using a Linux-distribution based on Debian (like Ubuntu), type the following lines into a terminal (The keyboard sequence to open a terminal in Linux usually is &lt;kbd&gt;Ctrl&lt;/kbd&gt;+&lt;kbd&gt;Alt&lt;/kbd&gt;+&lt;kbd&gt;T&lt;/kbd&gt;):
```bash
sudo apt update &amp;&amp; sudo apt upgrade -y
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.10
```


### Verify python installation
```bash
python3.10 --version
3.10.7
```
# Installation of Jupyter Lab

In the lecture and tutorials we use Jupyter Lab. To install it, open a terminal and enter ``pip install jupyterlab`` (Hint for macOS/Linux users: if this doesn&#39;t work, try ``pip3 install jupyterlab``. 

![](https://i.imgur.com/yOIycMj.png)

To open Jupyter Lab, type ``jupyter lab`` in your terminal. A new browser window pops up with jupyter lab running in the localhost. Don&#39;t close your terminal while working in jupyter lab. ([Here](https://jupyterlab.readthedocs.io/en/latest/user/interface.html) is the documentation of the Jupyter Lab Interface and how to use it)

# IDE
To write your own python code outside jupyter lab you can use any texeditor but we recommend to use an IDE (integrated development enviornment) which provides better syntax highlighting, text editing, debugging and many other helpful features.  
Some common IDEs:
* [Visual Studio Code](https://code.visualstudio.com/) (recommended)
* [Pycharm](https://www.jetbrains.com/de-de/pycharm/)
* [Sublime Text](https://www.sublimetext.com/)


# Success?

Was your python installation successful? 🐍
If you encountered any problems, please participate in the [feedbackr](https://www.fbr.io/info) and tell us what didn&#39;t work. 


&lt;!-- # Discord
For the question sessions and code reviews we use [Discord](https://discord.com/download). There is an in-browser version, but we highly recommend installing the desktop version, as it supports more features and options. After Installing Discord and setting up your account you can join our server through the following Link: https://discord.gg/UGSDbsz

Make sure your microphone/speaker/screen sharing/webcam (webcam is only needed during code reviews) work with discord. [Here](https://support.discord.com/hc/de/articles/360045138571-Beginner-s-Guide-to-Discord) is a tutorial.

When you first join the discord server you see the &#34;groupselection&#34; textchannel. Click on the green mark to select that you attend the course &#34;Informatics 2&#34;.

  ![](https://i.imgur.com/UGNuZX6.png)

  After that you have been granted the correct student role and you should see the following channels on the left side of discord:

  ![](https://i.imgur.com/ibXLIud.png)

  Those channels which are marked with a &#34;#&#34; symbol are text channels only (see 1, 2) and those channels with the &#34;&amp;#128266;&#34; symbol are voice channels only (see 3, 4).  

  1. The &#34;infos&#34; text channel is used by the tutors to communicate with students. (This is a read-only channel)
  2. The &#34;chat&#34; text channel can be used by students to ask questions during question hour.
  3. The &#34;Lobby&#34; voice channel is used by students to wait for their personal talk with a tutor, for example code reviews, very specific questions that can&#39;t be answerd in the TC Forum/question hour, ... (students have to enter this channel so tutors can see and move them to their private room)
  4. The &#34;TUTORIEN&#34; voice channels are used by the tutors for question hours (you can join them during question hour) --&gt;
