什麼是 GreyPandaMode
---
如果您的 EON 用的是灰熊(Grey Panda) 或 Harness，您可以讓 dragonpilot 裡的**tomtom/高德地圖/神盾 (或是其它的 GPS 應用程式)**使用高精度GPS數據。

優點：
1. 達到 10 公分以內的精度 (最佳狀況下)
2. 30 秒以內定位完成 (最佳狀況下)

缺點：
1. 斷開後無法定位
2. 可能不適用於其它應用程式


安裝方法
---
1. 請先確認您的 dragonpilot 在 0.6.4 以上或是最新的 devel 的版本
2. [SSH] 打開設定頁面: 
    ```bash
    am start -a android.settings.SETTINGS
    ```
3. [ANDROID] 找到「開發人員選項」，如果沒有此選項，請點選「關於手機」 > 然後連續點選「版本號碼」直到提示出現開啟為止。
4. [ANDROID] 點選「開發人員選項」
5. [ANDROID] 找到「選取模擬位置應用程式」
6. [ANDROID] 選擇
    ```bash
    cn.dragonpilot.gpsservice
    cn.dragonpilot.gpsservice
    ```
6. [SSH] 開啟 DragonGreyPandaMode 設定
    ```bash
    printf %s "1" > /data/params/d/DragonGreyPandaMode
    ```
7. [SSH] 重新開機
    ```bash
    reboot
    ```
    
反安裝方法
---
1. [SSH] 開閉 DragonGreyPandaMode 設定
    ```bash
    printf %s "0" > /data/params/d/DragonGreyPandaMode
    ```
2. [SSH] 打開設定頁面: 
    ```bash
    am start -a android.settings.SETTINGS
    ```
3. [ANDROID] 點選「開發人員選項」
4. [ANDROID] 找到「選取模擬位置應用程式」
5. [ANDROID] 選擇
    ```bash
    無
    ```
7. [SSH] 重新開機
    ```bash
    reboot
    ```

FAQ
---
```
Q. 一定只能在 dragonpilot 下用嗎？ 
A. 不用，您只要把 cn.dragonpilot.gpsservice 複制到您的 /data/openpilot/apk 然後照著上面的安裝方法即可，您可能需要手動啟動該服務。
```
```
Q. 它支援 XXXXXXXX 應用嗎？ 
A. 只要它允許使用「模擬位置應用程式」就行。
```
```
Q. 為什麼有時候 black 應用會有錯誤？
A. 因為 black 應用裡面調用了模擬位置的程式碼，若是沒有將它指定成為模擬位置應用程式的話，在運行時 Android 會強迫關閉它，重新進「選取模擬位置應用程式」勾選就行了。
```
```
Q. 為什麼設定好會後 dp 主畫面會顯示 Taoyuan City？
A. 這樣可以確定設定是成功的，然後我老家桃園 XD。
```