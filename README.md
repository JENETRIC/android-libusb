# libusb

[![Build Status](https://travis-ci.org/libusb/libusb.svg?branch=master)](https://travis-ci.org/libusb/libusb)
[![Build status](https://ci.appveyor.com/api/projects/status/xvrfam94jii4a6lw?svg=true)](https://ci.appveyor.com/project/LudovicRousseau/libusb)
[![Coverity Scan Build Status](https://scan.coverity.com/projects/2180/badge.svg)](https://scan.coverity.com/projects/libusb-libusb)

libusb is a library for USB device access from Linux, Mac OS X,
Windows, OpenBSD/NetBSD and Haiku userspace.
It is written in C (Haiku backend in C++) and licensed under the GNU
Lesser General Public License version 2.1 or, at your option, any later
version (see [COPYING](COPYING)).

libusb is abstracted internally in such a way that it can hopefully
be ported to other operating systems. Please see the [PORTING](PORTING)
file for more information.

libusb homepage:
http://libusb.info/

Developers will wish to consult the API documentation:
http://api.libusb.info

Use the mailing list for questions, comments, etc:
http://mailing-list.libusb.info

- Pete Batard <pete@akeo.ie>
- Hans de Goede <hdegoede@redhat.com>
- Xiaofan Chen <xiaofanc@gmail.com>
- Ludovic Rousseau <ludovic.rousseau@gmail.com>
- Nathan Hjelm <hjelmn@cs.unm.edu>
- Chris Dickens <christopher.a.dickens@gmail.com>

(Please use the mailing list rather than mailing developers directly)

## How To for Android

1. Search for the [UsbDevice] you are interested in.
2. Extract the usbfs `path` with [getDeviceName] from the [UsbDevice] object.
3. Build a `libusb_device` from the usbfs `path` using
   [libusb_get_device2\(context, path\)] from libusb.
4. Open the device with [openDevice] from [UsbDevice] object, you will get
   [UsbDeviceConnection] object.
5. From the [UsbDeviceConnection] object, extract the `fd` with
   [getFileDescriptor].
6. Now, from the `fd` and the previously created `libusb_device`, build a
   `libusb_device_handle` by calling [libusb_open2\(dev, handle, fd\)]
   from libusb.
7. And that all you need.

[UsbDevice]: http://developer.android.com/reference/android/hardware/usb/UsbDevice.html
[getDeviceName]: http://developer.android.com/reference/android/hardware/usb/UsbDevice.html#getDeviceName%28%29
[libusb_get_device2\(context, path\)]: https://github.com/kuldeepdhaka/libusb/blob/android-open2/libusb/core.c#L1492
[openDevice]: http://developer.android.com/reference/android/hardware/usb/UsbManager.html#openDevice%28android.hardware.usb.UsbDevice%29
[UsbDeviceConnection]: http://developer.android.com/reference/android/hardware/usb/UsbDeviceConnection.html
[getFileDescriptor]: http://developer.android.com/reference/android/hardware/usb/UsbDeviceConnection.html#getFileDescriptor%28%29
[libusb_open2\(dev, handle, fd\)]: https://github.com/kuldeepdhaka/libusb/blob/android-open2/libusb/core.c#L1267

