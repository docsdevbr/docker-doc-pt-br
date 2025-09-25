---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

title: Add or edit your run commands
description: Learn how to add or edit your run commands in Docker Projects
keywords: Docker, projects, docker deskotp, containerization, open, remote, local, run commands
weight: 40
---
## Add a run command to a project

1. Open an existing project and ensure that it is stopped.

2. From the command drop-down menu, select **New run command**.

3. Specify the following information for the run command:

   > [!TIP]
   >
   > While configuring your run command, you can view the equivalent `docker compose up` command in the **Run command** section on the configuration page. You can also use this command to run your project from the command line. You can refer to the [`docker compose up` reference documentation](/reference/cli/docker/compose/up.md) to learn more about the options you configure.

   - **Name**: Specify a name to identify the run command.
   - **Compose files**: Select one or more Compose files from your project.
   - **Flags**: Optionally, select one or more flags for your run command.

   > [!TIP]
   >
   > While the `--env-file` flag isn't currently supported, you can specify environment variables in your Compose file, or use the **Tasks** option to run a script that sets your environment variables.

   - **Services that will run**: After selecting one or more Compose files, the services defined in the files will appear here. If there is more than one service, you can optionally choose to not run a service by deselecting the checkbox.
   - **Tasks (Advanced options)**: Optionally specify a command to run before running the project. For example, if you want to run a bash script from the project directory named `set-vars.sh`, you can specify bash `set-vars.sh`. Or, on Windows, to run a script with `cmd.exe` named `set-vars.bat`, specify `set-vars.bat`. Note that a task can access environment variables from your terminal profile, but it can't access local shell functions nor aliases.

4. Select **Save changes**.

You can now select the new run command from the drop-down menu after opening the project.

## Edit a run command

1. Open an existing project and ensure that it is stopped.

2. Select the run command you want to change from the command drop-down menu.

3. Select the **Edit** icon next to the **Run** button.

4. Specify your changes and then select **Save changes**.

## What's next?

 - [Manage your projects](/manuals/projects/manage.md)
