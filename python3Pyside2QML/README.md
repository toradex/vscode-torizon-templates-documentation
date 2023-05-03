

# Python 3 Pyside 2(Qt 5) QML template specific documentation

How to create a virtual environment on this template:

 - On the terminal, run the command:

      `python -m venv .venv --system-site-packages`

      If you do not want to use Python packages installed with **apt** on your host remove the **--system-site-packages** argument. In this case, you have to include **debugpy** on the **requirements-debug.txt** file.

 - Press **F1**
 - Select the command **Python: Select Interpreter**
 - Select the Python interpreter of your **.venv** 
 - If it doesn't select the Python from the venv, press F1 and select the command
 **Developer: Reload Window**)

To install a Python package on the venv (and also on the Debug image), put it 
on the **requirements-debug.txt** file (to install it on the Release image put it
on the **requirements.release.txt** file)

For more details, please watch the demonstration video below:

<video controls width="90%">
  <source src="https://raw.githubusercontent.com/toradex/vscode-torizon-templates-documentation/main/common/python3/createEnvPython3-v2.mp4" type="video/mp4">
</video>

[](https://raw.githubusercontent.com/toradex/vscode-torizon-templates-documentation/main/common/python3/createEnvPython3-v2.mp4)

[The line above renders the video on GitHub but not on VSCode ]:<>

[As of now, the supported types of videos and audios are described in https://github.com/microsoft/vscode-docs/blob/vnext/release-notes/v1_72.md#built-in-preview-for-some-audio-and-video-files ]:<>
