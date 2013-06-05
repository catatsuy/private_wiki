# Android

## Android SDK

### UbuntuにてXperiaをデバッグモードできるようにする

`/etc/udev/rules.d/` に `51-android.rules` というファイル名のものを作成して

    SUBSYSTEM=="usb", ATTRS{idVendor}=="0fce", MODE="0666"

と書く もちろんroot権限 http://developer.android.com/guide/developing/device.html これに書いてある通り0fceはソニエリだけでHTC製とかならまた別らしい そしてroot権限で

    udevadm control --reload-rules
    /etc/init.d/udev restart

として再起動

それでAndroid SDK内の`platform-tools`ディレクトリをPATH通してから(もちろん通さなくてもプログラムを直接指定すればできるけど)

    adb kill-server
    adb start-server

をやる

    adb devices

と打って

    List of devices attached
    ????????????	no permissions

とか言われるようではダメで

    List of devices attached
    CB511GCW75	device

みたいな表示に変わるまでやる

### ネットに繋がらないとき

dnsをGoogleのやつにしてしまう adb shellして

    setprop net.dns1 8.8.8.8
    setprop net.dns2 8.8.4.4
