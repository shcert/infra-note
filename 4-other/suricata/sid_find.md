# rule
``` bash
grep '\bsid:[0-9][0-9]\?\b' suricata.rules
```

``` bash
# alert http any any -> any any (msg:"FILEEXT JPG file claimed"; fileext:"jpg"; sid:1; rev:1;)
# alert http any any -> any any (msg:"FILEEXT BMP file claimed"; fileext:"bmp"; sid:3; rev:1;)
# alert http any any -> any any (msg:"FILESTORE jpg"; flow:established,to_server; fileext:"jpg"; filestore; sid:6; rev:1;)
# alert http any any -> any any (msg:"FILESTORE pdf"; flow:established,to_server; fileext:"pdf"; filestore; sid:8; rev:1;)
# alert http any any -> any any (msg:"FILEMAGIC pdf"; flow:established,to_server; filemagic:"PDF document"; filestore; sid:9; rev:1;)
# alert http any any -> any any (msg:"FILEMAGIC jpg(1)"; flow:established,to_server; filemagic:"JPEG image data"; filestore; sid:10; rev:1;)
# alert http any any -> any any (msg:"FILEMAGIC jpg(2)"; flow:established,to_server; filemagic:"JFIF"; filestore; sid:11; rev:1;)
# alert http any any -> any any (msg:"FILEMAGIC short"; flow:established,to_server; filemagic:"very short file (no magic)"; filestore; sid:12; rev:1;)
# alert http any any -> any any (msg:"FILE store all"; filestore; noalert; sid:15; rev:1;)
# alert http any any -> any any (msg:"FILE magic"; filemagic:"JFIF"; filestore; noalert; sid:16; rev:1;)
# alert http any any -> any any (msg:"FILE magic"; filemagic:"GIF"; filestore; noalert; sid:23; rev:1;)
# alert http any any -> any any (msg:"FILE magic"; filemagic:"PNG"; filestore; noalert; sid:17; rev:1;)
# alert http any any -> any any (msg:"FILE magic -- windows"; flow:established,to_client; filemagic:"executable for MS Windows"; filestore; sid:18; rev:1;)
# alert http any any -> any any (msg:"FILE tracking PNG (1x1 pixel) (1)"; filemagic:"PNG image data, 1 x 1,"; sid:19; rev:1;)
# alert http any any -> any any (msg:"FILE tracking PNG (1x1 pixel) (2)"; filemagic:"PNG image data, 1 x 1|00|"; sid:20; rev:1;)
# alert http any any -> any any (msg:"FILE tracking GIF (1x1 pixel)"; filemagic:"GIF image data, version 89a, 1 x 1|00|"; sid:21; rev:1;)
# alert http any any -> any any (msg:"FILE pdf claimed, but not pdf"; flow:established,to_client; fileext:"pdf"; filemagic:!"PDF document"; filestore; sid:22; rev:1;)
# alert smtp any any -> any any (msg:"File Found over SMTP and stored"; filestore; sid:27; rev:1;)
# alert http any any -> any any (msg:"Black list checksum match and extract MD5"; filemd5:fileextraction-chksum.list; filestore; sid:28; rev:1;)
# alert http any any -> any any (msg:"Black list checksum match and extract SHA1"; filesha1:fileextraction-chksum.list; filestore; sid:29; rev:1;)
# alert http any any -> any any (msg:"Black list checksum match and extract SHA256"; filesha256:fileextraction-chksum.list; filestore; sid:30; rev:1;)
# alert ftp-data any any -> any any (msg:"File Found within FTP and stored"; filestore; filename:"password"; ftpdata_command:stor; sid:31; rev:1;)
# alert smb any any -> any any (msg:"File Found over SMB and stored"; filestore; sid:32; rev:1;)
# alert nfs any any -> any any (msg:"File found within NFS and stored"; filestore; sid:33; rev:1;)
```

dlp rule,  
스테가노 그라피,  
파일의 checksum 검사,  이런게 주류인 default rule인듯  
성격을 보면은 1~100까진 파일검사를 위한 rule인듯  
