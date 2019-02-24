# DeltaOS
<img src="https://imgur.com/89gDgc3.png">
Get the change you need from your phone

### Building Requirements
- At least 70GB of disk space
- A lot of internet (like 20GB) to download the source
- A computer with a linux based os with at least 8GB of RAM
- Patience. A lot of patience

### Instructions
- Downloading the source
    1. Make sure you setted up a build environment for rom compiling
    2. Create a new direcory and inside of it run these commands in order:
        ```
        repo init -u https://github.com/DeltaOpenSourceProject/manifest -b deltapie
        repo sync -jx -f -c --force-sync --no-tags --no-clone-bundle
        //Where x is the number of cores of your cpu
        ```
    3. You're set up for the ROM source, time to set up the device one

- Downloading and setting up the device source
    1. Add all your device relevant repos in `.repo/local_manifests/local_manifests.xml`
    2. Run `repo sync -jx -f -c --force-sync --no-tags --no-clone-bundle`
    3. Move/copy your `<ROM>.mk` (Example: `lineage.mk`, `aosp_chiron.mk`) file to `delta.mk`
    4. Open the mentioned file and
        - Set PRODUCT_NAME to `delta_<device>` (Example: `delta_chiron`)
        - For a Phone or tablet with a SIM Card, add
            ```
            # Inherit from Delta vendor
            $(call inherit-product, vendor/delta/config/common_full_phone.mk)
            ```
        - For a WiFi-only tablet, add
            ```
            # Inherit from Delta vendor
            $(call inherit-product, vendor/delta/config/common_full_tablet_wifionly.mk)
            ```
    5. Save and exit

- Building the rom
    1. Run
        ```
        source build/envsetup.sh;
        add_lunch_combo delta_<device>-userdebug;
        brunch <device>;
        ```
        Example:
        ```
        source build/envsetup.sh;
        add_lunch_combo delta_chiron-userdebug;
        brunch beryllium;
        ```
    2. Now you just have to wait, go get a coffee (a veeeeryyy long one), read a book, watch some Netflix or youtube, anything to fill the time gap
    3. Resolve errors if any, deal with the pain and continue building

### For dealing with compilation pain
- You can contact the Delta team on [**Telegram**](https://t.me/DeltaOSCommunity)
- If you need to solve any common porting problem try to ask on [**Android Building Help**](https://t.me/AndroidBuildersHelp)
- Make sure you provide relevant logs, screenshots and details with all sources you used.

### Adding your own device as official
- For adding your device to the list of supported devices, please reach us at [**Telegram**](https://t.me/DeltaOSCommunity) with your device tree and previous works.

Credits
-------
 * [**AOSP**](https://android.googlesource.com)
 * [**AOSiP**](https://github.com/AOSiP)
 * [**LineageOS**](https://github.com/LineageOS)
 * [**POSP**](https://github.com/PotatoProject)
 * [**NitrogenProject**](https://github.com/nitrogen-project)
