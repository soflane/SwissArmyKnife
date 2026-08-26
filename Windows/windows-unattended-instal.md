# Windows Unattended instal

# Windows automated install

## **1. Generate Answer File**

Go to [Windows Answer File Generator](https://www.windowsafg.com/), select the Windows version you wish to use generate your answer file. Help and explaination about the settings can be found [here](https://www.windowsafg.com/tutorial.html).

As a reminder, depending on the version of Windows you wish to use, generic keys can be provided during the installation. They do not activate the system but allow to skip this step :

* **Windows 10 home :**

```xml
TX9XD-98N7V-6WMQ6-BX7FG-H8Q99
```

* **Windows 10 Pro :**

```xml
VK7JG-NPHTM-C97JM-9MPGT-3V66T
```

* **Windows 10 Enterprise :**

```xml
NPPR9-FWDCX-D2C8J-H872K-2YT43
```

* **Windows 10 Home (single langue) :**

```xml
7HNRX-D7KGG-3K4RQ-4WPJ4-YTDFH
```

When you have answered all the questions, hit the 'Download File' link. It will give you a `autounattend.xml` file.

## **2. Copy answer file**

This file you've just downloaded have to be put in the root folder of your installation media :

* Install via USB

Burn your ISO file to your USB key (with apps like Rufus, or BalenaEtcher) Then, simply copy the `autounattend.xml` file in the root of your USB media.

* Install via ISO

You'll have to recreate a new ISO image with that file. I would recommend Anyburn for that operation, as it is free.

## **3. Copy custom files**

### **The $$ Folder**

The subfolder :

```xml
sources\$OEM\$$ 
```

Will write contents to the folder :

```xml
C:\Windows
```

For example :

```xml
sources\$OEM$\$$\Web\Wallpaper\Dell 
```

Will write :

```xml
C:\Windows\Web\Wallpaper\Dell 
```

### **The $1 folder**

The folder :

```xml
sources\$OEM$\$1
```

On the other hand will write directly to :

```xml
C:\
```

Example:

```xml
 sources\$OEM$\$1\setup\apps\x64
```

This gives the following :

```xml
C:\setup\apps
```