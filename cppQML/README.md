# C++ Qt 6 QML Template Specific Documentation

All projects follow the pipeline of tasks described in the [common contributing documentation](https://github.com/toradex/vscode-torizon-templates/blob/bookworm/CONTRIBUTING.md#contributing-templates). However, each project has its own specificities in terms of technologies and methods used to compile, deploy, and debug the code. Therefore, each of them has their own specific tasks in the **tasks.json** file.

This C++ Qt 6 QML template uses **cmake** and **make** to compile the code, with tasks named **build-configure-\${architecture}** (creates the destination directory for the future compiled code and generates the Makefile, using **cmake**) and **build-debug-\${architecture}** (compiles the code). It also uses an SDK container to compile the code (through armhf and arm64 emulation). This container image is built using the **Dockerfile.sdk** file, and the tasks that build the containers are named **build-container-image-sdk-\${architecture}**.

The compiled code is then copied into the running debug container using **scp**, in the task named **deploy-torizon-\${architecture}**. This task contains the entire sequence of tasks executed by the pipeline and, therefore, is unique to each template.

Finally, remote debugging is performed by attaching to the GDB on the running container on the device using a [VSCode feature called Pipe Transport](https://code.visualstudio.com/docs/cpp/pipe-transport). For local debugging, the [VSCode method for C/C++ Debugging](https://code.visualstudio.com/docs/cpp/launch-json-reference) is used. The tasks that perform the debugging are those present in the **launch.json** file.


The source code of the template is inspired by the one created using [the examples present on Qt Creator](https://doc.qt.io/qt-6/qtexamplesandtutorials.html), customizing it to a Torizon Qt QML (sort of Hello World) application. Also taking inspiration on examples present in the Qt documentation, like in the [CMake Build QML part](https://doc.qt.io/qt-6/cmake-build-qml-application.html).

## Qt Creator and Qt Design Studio

You can install Qt features though **apt**, by installing packages like **qt6-base-dev** and **qt6-declarative-dev**, recommended by **check-deps**. However, to ensure better functionality on the Local Debug modes, it is recommended to install Qt through [their webpage](https://www.qt.io/download), even the free version.

You can open your application on Qt Creator and Qt Design Studio using the tasks **open-in-qt-creator** and **open-in-qt-design-studio**.

Also, it is possible to debug the application (including the QML part) on Qt Creator, through the task **start-gdb-server-\<remote or local>-\${architecture}**. To do it, follow this steps:

 - Open the project on Qt Creator, through the **open-in-qt-creator-debug\${architecture}** task (**open-in-qt-creator** for local debug). It is necessary to open Qt Creator through this task.
 - Run the **start-gdb-server-\<remote or local>-\${architecture}** task
 - On Qt Creator, **Attach to Running Debug Server** (or **Attach to QML Port** for debugging the QML):

    ![](https://raw.githubusercontent.com/toradex/vscode-torizon-templates-documentation/main/cppQML/attachDebug.png)

 - Confirm the debugging information and press **Ok**:

    ![](https://raw.githubusercontent.com/toradex/vscode-torizon-templates-documentation/main/cppQML/checkInfoAttachDebug.png)

## .gitignore and the .qt directory

For opening the project on Qt Creator it is necessary to have this **.qt** directory, with the initial files and folders present in it. So, you need to commit at least this initial **.qt** directory to your Git repository.

But literally almost anything you do on Qt Creator (like dragging the Qt Creator window for example) modifies this files, and this will be shown as modifications on Git. So, after you have committed the **.qt** file once, you can uncomment the **.qt** line from the **.gitignore** file.

