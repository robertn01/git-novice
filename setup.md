---
layout: page
title: Setup
permalink: /setup/
---

<div id="git"> <!-- Start of 'Git' section. GitHub browser compatability
           is given at https://help.github.com/articles/supported-browsers/-->
  <h3>GitHub</h3>
  <p>
    You will need an account at <a href="https://github.com/">github.com</a>
    for the Git lesson. Basic GitHub accounts are free, so please create one if you haven't already.
    You should also consider what personal information you'd like to reveal. For
    example, you may want to review
    <a href="https://help.github.com/articles/keeping-your-email-address-private/">these instructions</a>
    for keeping your email address private.
  </p>
</div> <!-- End of 'Git' section. -->

<!-- Commenting out what won't be used in a lab with Python and Git already installed
<div id="python"> <!-- Start of 'Python' section. Remove the third paragraph if
           the workshop will teach Python using something other than
           the IPython notebook.
           Details at http://ipython.org/ipython-doc/2/install/install.html#browser-compatibility -->
  <h3>Python</h3>

  <p>
    <a href="http://python.org">Python</a> is a popular language for general-purpose
    programming that has been widely adopted for scientific computing. Unfortunately, installing all of
    its scientific packages individually can be difficult, so we will be relying on an
    all-in-one installer called <a href="https://www.continuum.io/anaconda">Anaconda</a>.
   </p>
    <p>
      <strong>For all instructions below, please ensure you install Python version 3</strong>
    </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="python-windows">Windows</h4>
      <!-- <a href="https://www.youtube.com/watch?v=xxQ0mzZ8UvA">Video Tutorial</a> -->
      <ol>
        <li>Open <a href="https://conda.io/miniconda.html">https://conda.io/miniconda.html</a> with your web browser.</li>
        <li>Download the Python 3 installer for Windows.</li>
        <li>Install Python 3 using all of the defaults for installation. Make sure the
          <strong>Register Anaconda as my default Python</strong> checkbox is selected before clicking 'Install'.</li>
      </ol>
    </div>
    <div class="col-md-4">
      <h4 id="python-macosx">Mac OS X</h4>
      <!-- <a href="https://www.youtube.com/watch?v=TcSAln46u9U">Video Tutorial</a> -->
      <ol>
        <li>Open <a href="https://www.continuum.io/downloads">https://www.continuum.io/downloads</a> with your web browser.</li>
        <li>Download the Python 3 installer for OS X.</li>
        <li>Install Python 3 using all of the defaults for installation.</li>
      </ol>
    </div>
    <div class="col-md-4">
      <h4 id="python-linux">Linux</h4>
      <ol>
        <li>Open <a href="https://conda.io/miniconda.html">https://conda.io/miniconda.html</a> with your web browser.</li>
        <li>Download the Python 3 installer for Linux.</li>
        <li>Install Python 3 using all of the defaults for installation.
        (Installation requires using the shell. If you aren't
        comfortable doing the installation yourself
        stop here and request help at the workshop.)</li>
        <li>
          Open a terminal window.
        </li>
        <li>
          Type <pre>bash Miniconda3-</pre> and then press
          tab. The name of the file you just downloaded should
          appear.
        </li>
        <li>
          Press enter. You will follow the text-only prompts.  When
          there is a colon at the bottom of the screen press the down
          arrow to move down through the text. Type <code>yes</code> and
          press enter to approve the license. Press enter to approve the
          default location for the files. Type <code>yes</code> and
          press enter to prepend Anaconda to your <code>PATH</code>
          (this makes the Anaconda distribution the default Python).
        </li>
      </ol>
    </div>
  </div>
</div> <!-- End of 'Python' section. -->

<div id="shell"> <!-- Start of 'shell' section. -->
  <h3>The Bash Shell, Jupyter, and Git</h3>
    <ul>
      <li>Bash is a commonly-used shell that gives you the power to do simple
        tasks more quickly.</li>
      <li>Git is a version control system that lets you track who made changes
    to what and has options for easily updating a shared or public
    version of your code
    on <a href="https://github.com/">github.com</a>.</li>
    <li>We will teach Python using the Jupyter notebook, a programming environment
      that runs in a web browser. For this to work you will need a reasonably
      up-to-date browser. The current versions of the Chrome, Safari, and
      Firefox browsers are all
      <a href="http://ipython.org/ipython-doc/2/install/install.html#browser-compatibility">supported</a>
      (some older browsers, including Internet Explorer version 9
      and below, are not).</li>
  </ul>

  <div class="row">
    <div class="col-md-4">
      <h4 id="shell-windows">Windows</h4>
      <ol>
        <li>Open a command prompt
          <ul><li>Open Start Menu </li>
            <li>type <code>cmd</code></li>
            <li>press [Enter]</li></ul>
          </li>

        <li>
              Type the following lines into the command prompt window one at a time exactly as shown, hitting [Enter]
          after each one.
          <pre>
conda create -n bash m2-base git jupyter pandas tornado=4.4 console_shortcut

activate bash

conda install -c swc nano</pre>

          Continue to press [Enter] at any prompts and wait for the 'C:\' to return after
          each command before progressing (<strong>the first step can take many minutes
          and look like it's stuck, so please be patient</strong>).
        </li>

        <li>
          You should now be able to find a new folder in your Start menu called 'Anaconda'. Inside the folder will
          be two 'Anaconda Prompt' programs. Choose the one that doesn't say '(bash)'
          </li>
        <li>Activate the correct conda environment by typing:
        <pre>activate bash</pre>
        </li>
      </ol>
      <br/>Optionally, <a href="http://cmder.net/">Cmder</a> is a (much) nicer terminal environment for Windows.
    </div>
    <div class="col-md-4">
      <h4 id="shell-macosx">Mac OS X</h4>
      <p>
        The default shell in all versions of Mac OS X is Bash.
      </p>
      <ol>
        <li>Open the 'Terminal' program (found in <code>/Applications/Utilities</code>).</li>
        <li>Type the following into the Terminal command prompt window exactly as shown:
          <pre>conda install git jupyter pandas</pre></li>
      </ol>
        <br/>Optionally, <a href="https://www.iterm2.com/">iTerm2</a> is a more feature-rich terminal environment that is
        a little easier on the eyes.
    </div>
    <div class="col-md-4">
      <h4 id="shell-linux">Linux</h4>
      <p>
        The default shell is usually Bash, but if your machine is set up
        differently you can run it by opening a terminal and typing <code>bash</code>.
      </p>
      <ol>
        <li>Open the Terminal</li>
        <li>Type the following into the command prompt window exactly as shown:
          <pre>conda install git jupyter pandas</pre></li>
      </ol>
    </div>
  </div>
</div> <!-- End of 'shell' section. -->
-->
