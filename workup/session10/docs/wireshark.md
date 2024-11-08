[Main Menu](../../README.md) | [session10](../../session10/) | [Wireshark](../docs/wireshark.md)


# Examining packets using wireshark

See tutorial on [Wireshark on Raspberry Pi](https://pimylifeup.com/raspberry-pi-wireshark/)

## to install wireshark in a raspberry pi

```
sudo apt install wireshark
```

a splash screen will ask `should non superuser users be able to capture packets` - answer yes.

Add the `admin` user to the `wireshark` group 

```
sudo usermod -a -G wireshark admin
```

After this `reboot` the system.

## with no Internet connection

Alternatively, if your Internet connection is slow or not working you can install directly from files which have been downloaded in advance.
Download (or transfer using a USB memory stick) the following files to your Pi:

```
sudo apt clean
sudo apt install --download-only wireshark
```
downloads the following packages to `/var/cache/apt/archives`

```
libbcg729-0_1.1.1-2_armhf.deb
libc-ares2_1.18.1-3_armhf.deb
libmaxminddb0_1.7.1-1_armhf.deb
libminizip1_1.1-8+deb12u1_armhf.deb
libqt5multimedia5_5.15.8-2_armhf.deb
libqt5multimedia5-plugins_5.15.8-2_armhf.deb
libqt5multimediagsttools5_5.15.8-2_armhf.deb
libqt5multimediaquick5_5.15.8-2_armhf.deb
libqt5multimediawidgets5_5.15.8-2_armhf.deb
libsmi2ldbl_0.4.8+dfsg2-16_armhf.deb
libwireshark16_4.0.11-1~deb12u1_armhf.deb
libwireshark-data_4.0.11-1~deb12u1_all.deb
libwiretap13_4.0.11-1~deb12u1_armhf.deb
libwsutil14_4.0.11-1~deb12u1_armhf.deb
wireshark_4.0.11-1~deb12u1_armhf.deb
wireshark-common_4.0.11-1~deb12u1_armhf.deb
wireshark-qt_4.0.11-1~deb12u1_armhf.deb
```
to install, copy packages onto a usb drive and move to your pi.
Then use;

```
sudo apt-get install -f ./*.deb
```
