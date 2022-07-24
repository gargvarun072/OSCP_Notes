VHD Enumeration

VHD Enumeration

# VHD Enumeration

#### VHD Listing 
`7z l temp.vhd` 



### Mount VHD to linux directory 
`apt-get install libguestfs-tools` 
`Guestmount –add *.vhd --inspector –ro –v /mnt/vhd` 