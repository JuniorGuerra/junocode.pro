---
title: "How to create a desktop entry in linux"
date: 2024-05-20T08:06:25+06:00
description: Creation of Desktop Entry in Linux
menu:
  sidebar:
    name: Desktop Entry
    identifier: desktop-entry
    weight: 10
tags: ["Basic", "Linux", "Desktop"]
categories: ["Basic"]
---

If you use Linux as your primary operating system, you might have noticed that some downloaded applications do not come with a predefined desktop entry. This is common when we download applications in `.tar.gz` format that do not include specific instructions for automatic system integration.

Fortunately, Linux allows us to create our own desktop entries so these applications appear in the application search. In this tutorial, you will learn how to create a `name_file.desktop` file to achieve this.

We will take Postman as an example, an application that is downloaded as a `.tar.gz` file and does not automatically create a desktop entry when unzipped. Follow these simple steps to manually configure the entry.

## Creating a `.desktop` file

### Step 1: Create the `.desktop` file

We are going to create a new `.desktop` file. Since our example is with Postman, we will call it `postman.desktop`.

The file must include the following keys:

- `[Desktop Entry]`: Indicates that we are creating a desktop entry.
- `Name`: The name of the application.
- `Exec`: The path where the executable is located.
- `Type`: The type of application.
- `Icon`: The path of the application icon.

### Optional

These fields are optional but provide more information and improve integration:

- `Comment`: A brief description of the application.
- `Categories`: Categories of the application.
- `GenericName`: Generic name of the application.
- `Path`: The path where the application is located.

### Step 2: Configure the file

We must create the file in `/usr/share/applications` to make it available to all users. If you do not have superuser permissions, you can create it in `~/.local/share/applications`.

To create the file, use your preferred text editor. Here we use `vim` as an example. If you don't have it installed, you can do so with `sudo apt install vim`.

```sh
sudo vim /usr/share/applications/postman.desktop
```

Add the following configuration to the file:

```ini
[Desktop Entry]
Name=Postman
Comment=Test endpoint
GenericName=Internet API TEST
Exec=/usr/share/Postman/Postman
Icon=/usr/share/Postman/postman.png
Type=Application
Categories=Network;InstantMessaging;
Path=/usr/share/Postman
```

Save and close the file by pressing `Esc` and then typing `:wq`.

### Step 3: Assign permissions

Once finished, we can validate if it works and, if necessary, assign execution permissions to the file:

```sh
chmod +x /usr/share/applications/postman.desktop
```

### Step 4: Refresh the desktop environment

If your machine does not recognize the changes in real time, you can refresh the desktop environment:

```sh
sudo update-desktop-database
```

By following these steps, you will have created a desktop entry for Postman that will appear in your Linux desktop environment's application search. This technique can be applied to any other application that needs a custom desktop entry.