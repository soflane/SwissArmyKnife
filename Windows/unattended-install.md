# Create an unattended Windows installation

> Add an answer file and optional custom files to Windows installation media so
> setup can run with fewer manual prompts.

## Prerequisites

- A Windows ISO that matches the edition you intend to install.
- A USB drive or an ISO-editing tool.
- A valid Windows license for the target device.
- A safe test device or virtual machine.

The generic installation keys below select an edition but do not activate
Windows:

```text
Windows 10 Home:                 TX9XD-98N7V-6WMQ6-BX7FG-H8Q99
Windows 10 Pro:                  VK7JG-NPHTM-C97JM-9MPGT-3V66T
Windows 10 Enterprise:           NPPR9-FWDCX-D2C8J-H872K-2YT43
Windows 10 Home Single Language: 7HNRX-D7KGG-3K4RQ-4WPJ4-YTDFH
```

## Steps

### 1. Generate the answer file

1. Open the [Windows Answer File Generator](https://www.windowsafg.com/).
2. Select the Windows edition used by the installation media.
3. Review every generated setting; use the site's
   [tutorial](https://www.windowsafg.com/tutorial.html) when a field is unclear.
4. Download the generated file and keep its name as `autounattend.xml`.

An answer file can contain passwords, product keys, and other sensitive data.
Inspect it before committing or sharing it, and never add a personalized answer
file to this public repository.

### 2. Add the answer file to the installation media

For a USB installation:

1. Write the Windows ISO to a USB drive with a tool such as
   [Rufus](https://rufus.ie/).
2. Copy `autounattend.xml` to the root of the USB drive.

For an ISO installation, use an ISO editor to add `autounattend.xml` to the root
of a copy of the image, then save a new ISO. Keep the original ISO unchanged.

### 3. Add optional custom files

Windows Setup copies files from special folders under `sources\$OEM$`.

Files under this folder:

```text
sources\$OEM$\$$
```

are copied into:

```text
C:\Windows
```

For example:

```text
sources\$OEM$\$$\Web\Wallpaper\Dell
```

becomes:

```text
C:\Windows\Web\Wallpaper\Dell
```

Files under this folder:

```text
sources\$OEM$\$1
```

are copied to the system drive. For example:

```text
sources\$OEM$\$1\setup\apps\x64
```

becomes:

```text
C:\setup\apps\x64
```

## Verify

1. Boot the media in a disposable virtual machine before using it on physical
   hardware.
2. Confirm that Setup selects the intended edition and locale.
3. Confirm that every automated answer is appropriate for the target system.
4. Check that optional files appear under `C:\Windows` or `C:\` as expected.
5. Stop the deployment if Setup selects or formats an unexpected disk.

## References

- [Windows Answer File Generator](https://www.windowsafg.com/)
- [Windows Answer File Generator tutorial](https://www.windowsafg.com/tutorial.html)
- [Rufus](https://rufus.ie/)
