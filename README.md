### These commands show how to build an OpenWrt package(ipk) of apfree_wifidog
<pre>
cd openwrt

echo "src-git apfree https://github.com/KunTengRom/packages.git;for-wifidog" >> feeds.conf.default

./scripts/feeds update apfree
./scripts/feeds install -a -p apfree
</pre>

The apfree_wifidog packages should now appear in menuconfig.

<pre>
make menuconfig

Network  ---> Captive Portals  ---> < M > apfree_wifidog

LuCI  ---> 3. Applications  ---> <*> luci-app-apfree_wifidog
</pre>

Exit and save the settings. Then build the packages:

<pre>
make package/apfree_wifidog/compile V=s
make package/luci-app-apfree_wifidog/compile V=s
</pre>

The ipk packages can now be found in `bin/.../packages/apfree/`
