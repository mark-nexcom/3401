準備一台x86設備，並安裝Ubuntu18.04以上的系統，磁片可用空間大於30G,若使用SDKmanager安裝CUDA等庫，則需要磁片可用空間大於50G
1.	打開https://developer.nvidia.com/embedded/linux-tegra-r32.4.3
2.	下載BSP文件和跟檔案系統：
 ![image](https://github.com/mark-nexcom/3401/assets/63223264/7e19e009-be88-43b3-a78c-0aa3ae67e3ea)
3.	拷貝提供的其它檔到與第二步下載的位置同一資料夾下（如果提供的檔中中有system.img,資料夾所在的分區可用空間能夠放下這些檔即可，否則該分區的可用空間需要大於30G）
4.	解壓下載的BSP文件tar -xvf xxx-aarch.tbz2（不需要使用sudo）
5.	解壓Sample Root Filesystem檔（需要加上sudo）到4步解壓的資料夾（Linux_for_Tegra）下的rootfs下（需要使用sudo）
6.	在Linux_for_Tegra下執行sudo ./apply_binaries.sh
7.	在Linux_for_Tegra下執行燒錄命令
重構：sudo ./flash.sh jetson-nano-emmc mmcblk0p1
不重構：sudo ./flash.sh –no-systemimg jetson-nano-emmc mmcblk0p1
提示：不提供system.img需要重構（該過程耗時，第一次重構後，後面可以不用重構），  提供xxx.img鏡像選擇不重構
8.	系統備份：
在Linux_for_Tegra下執行燒錄命令（設備需要進入到復原模式，xxx.img-----備份的鏡像）
sudo ./flash.sh -r -k APP -G xxx.img jetson-nano-emmc mmcblk0p1
