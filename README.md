# AIOT ESP32—復原初始眼睛辨識（Windows）

## 目錄
#### [ESP32S3 簡介](https://hackmd.io/zI9JMEdBTy2z-ektNHygmA?edit)
#### [ESP-IDF 安裝及環境建置（Hello World）（Win）](https://hackmd.io/tRP9xLiiQpmnTxIsSlCNLw?view)
#### >> [復原眼睛辨識（Win）](https://hackmd.io/pgEcdY5JRlq2X1GM3NILmw?view)

## 復原初始眼睛辨識（Win）
（以 ESP32S3 晶片在Windows環境下的設定為例）

1. 執行 ESP-IDF CMD

（**以下 2~3 步若先前已執行則可省略，直接進行第 4 步。**）

2. 終端機輸入指令進入資料夾
   `<D:\ESPIDF\Espressif\frameworks\esp-idf-v5.2.1\examples>`
   ```
   cd frameworks\esp-idf-v5.2.1\examples
   ```
   
3. 終端機輸入指令 Clone ESP-WHO Espressif 檢測識別庫
   ```
   git clone --recursive https://github.com/espressif/esp-who.git
   ```

4. 終端機輸入指令進入資料夾 `<D:\ESPIDF\Espressif\frameworks\esp-idf-v5.2.1\examples\esp-who\examples\esp32-s3-eye>`
    ```
    cd frameworks\esp-idf-v5.2.1\examples\esp-who\examples\esp32-s3-eye
    ```
    
5. 終端機輸入指令將晶片設定為 esp32s3
    ```
    idf.py set-target esp32s3
    ```
6. 終端機輸入指令清除先前配置
    ```
    idf.py fullclean
    ```

7. 終端機輸入指令編譯燒錄工程
    ```
    idf.py build
    ```
    
8. 編譯後終端機顯示
    ```
    Project build complete. To flash, run:
     idf.py flash
    or
     idf.py -p PORT flash
    or
     python -m esptool --chip esp32s3 -b 460800 --before default_reset --after hard_reset --no-stub write_flash --flash_mode dio --flash_size 8MB --flash_freq 80m 0x0 build\bootloader\bootloader.bin 0x8000 build\partition_table\partition-table.bin 0x10000 build\esp32-s3-eye.bin 0x3f8000 build\srmodels\srmodels.bin
    or from the "D:\ESPIDF\Espressif\frameworks\esp-idf-v5.2.1\examples\esp-who\examples\esp32-s3-eye\build" directory
     python -m esptool --chip esp32s3 -b 460800 --before default_reset --after hard_reset --no-stub write_flash "@flash_args"
    ```
    ![終端機輸出編譯成功](https://hackmd.io/_uploads/SkvwgZlHA.png)

9. 16. 終端機輸入指令下載 hello world 程序到開發板（`COM3` 依電腦接口自訂）
    ```
    idf.py -p COM3 flash 
    ```
    
10. 眼睛偵測出現於開發版（按下開發版 MENU 鍵）

11. 終端機輸入指令監視輸出
    ```
    idf.py monitor
    ```

12. 輸出影像結果顯示於晶片螢幕及終端機
    ![終端機輸出](https://hackmd.io/_uploads/ByPyMblB0.png)
    
    ![終端機及晶片螢幕輸出](https://hackmd.io/_uploads/ByRszWlSR.jpg)

## 附加資源
- [ESP-IDF 編程指南](https://espressif-docs.readthedocs-hosted.com/projects/esp-idf/zh-cn/latest/get-started/index.html) 

## 參考資料
- [AIoT_two，itemhsu](https://github.com/itemhsu/AIoT_two) 
