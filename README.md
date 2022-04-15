# Puffco-Firmware-Authentication
Code to decrypt new Firmware X authentication allowing read/write access over bluetooth.

As puffco released Firmware X to break my puffmods website, I did some deobfuscation and found the function that does everything I needed.

# How their authentication works

1. read AccessSeedKey from device. This is different every time you connect.
2. Create a 32 bit Uint8Array
3. Add DEVICE_HANDSHAKE to the first 16 bits of the Uint8Array
4. Add AccessSeedKey to last 16 bits of the 32 bit Uint8Array
5. Hash Uint8Array with sha256 and convert that hex string to a num array
6. Slice 32 bit key into 16 bit (First 16)
7. Write new AccessSeedKey to device
8. You now have read/write to bluetooth characteristics!!

Thanks to puffco for adding something new in their firmware just for me! It was a fun several hours of playing around.

If you have any questions regarding anything puffco related. Message me on discord: Fr0st3h#9889
