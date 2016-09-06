# Extensions for enterprise
Microsoft Edge extensions have a similar workflow when compared to other enterprise UWP apps. The information below details enterprise specific aspects of Microsoft Edge extensions.


## Windows Information Protection
Microsoft Edge extensions currently don't honor Windows Information Protection (WIP) settings. If an enterprise is concerned about data protection, extensions support should not be enabled for Microsoft Edge.

To disable extensions for employees, configure Group Policy and Microsoft Intune settings. For more info on which policies to configure, see [Available policies for Microsoft Edge](https://technet.microsoft.com/en-us/itpro/microsoft-edge/available-policies).


## Packaging extensions

Before an enterprise can distribute an extension to its employees, it must first be packaged. Instructions on packaging extensions are available through the Technology Adoption Program (TAP).


## Distributing extensions

Once an extension has been packaged, it can be distributed to employees through the Windows Store, Windows Store for Business, or by sideloading.

Extensions distributed though the Windows Store for Business can either be assigned to employees, or added to a private store where all employees can access them. This can be done by following the [Distribute "Line-of-Business" (LOB) apps to enterprises](https://msdn.microsoft.com/windows/uwp/publish/distribute-lob-apps-to-enterprises) guide.

To sideload extensions, devices (unmanaged or managed) must be unlocked for sideloading. See [Sideload LOB apps in Windows 10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10) for more info on how to sideload packaged extensions.


### Behavior of sideloaded extensions

Unlike extensions distributed through the Windows Store (or the Windows Store for Business), sideloaded extensions are treated differently in Microsoft Edge.

The first difference affects how sideloaded extensions behave after installation. Unlike extensions from the Windows Store, sideloaded extensions do not immediately display the "You have a new extension" notification and need to be manually turned on by the user.

To turn on the extension, open the **More (...)** menu, select **"Extensions"** and you should see the sideloaded extension in the list of installed extensions. Click on the extension and turn it on.

The second difference affects how sideloaded extensions appear in the browser. For example, both the "You have a new extension" notification and the list of installed extensions include an additional warning stating that the extension is from an unknown source.

![sideload warning 1](../media/sideload-permissionflyout.PNG)

![sideload warning 2](../media/sideload-l1warning.PNG)

The third and final difference affects how sideloaded extensions behave on browser startup. Sideloaded extensions on devices that are either domain-joined or MDM enabled will behave like extensions from the Windows Store. However, sideloaded extensions on devices that are not domain-joined or MDM enabled will be turned off during browser startup and require the user to take explicit action.

Shortly after browser startup (after ~10 seconds of inactivity) the following notification will appear near the bottom of the window.

![sideload notification](../media/sideload-scareUI.PNG)

Each time Microsoft Edge is launched, users will need to select "Turn on anyway" in order to use the extension.
