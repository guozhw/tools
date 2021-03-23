# C:\windows\SYSTEN32\atiadlxx.dll 没有被指定在 Windows 上运行
启动开始菜单，输入 “cmd”，右键以管理员身份运行，依次执行以下 2 条命令：
for %i in (%windir%\system32\*.dll) do regsvr32.exe /s %i
for %i in (%windir%\system32\*.ocx) do regsvr32.exe /s %i

执行完毕后重启设备，在管理员 cmd 中继续依次执行下方 4 条命令：
Dism /Online /Cleanup-Image /ScanHealth
Dism /Online /Cleanup-Image /CheckHealth
DISM /Online /Cleanup-image /RestoreHealth
sfc /SCANNOW

执行完毕后第二次重启设备，看一下是否还会出现 “C:\windows\SYSTEN32\atiadlxx.dll 没有被指定在 Windows 上运行” 的错误提示。

# [Access Linux filesystems in Windows and WSL 2 (preview)](https://docs.microsoft.com/en-us/windows/wsl/wsl2-mount-disk)
note: Windows 10 Insider Preview Build 20211
Mounting an unpartitioned disk
``` PowerShell
wmic diskdrive list brief    # To list the available disks in Windows
wsl --mount <DiskPath>
```
Mounting a partitioned disk
``` PowerShell
wmic diskdrive list brief    # To list the available disks in Windows
wsl --mount <DiskPath> --bare
blkid <BlockDevice> # Identifying the filesystem type
```
Mount the selected partitions
``` PowerShell
wsl --mount <DiskPath> --partition <PartitionNumber> --type <Filesystem>
```
