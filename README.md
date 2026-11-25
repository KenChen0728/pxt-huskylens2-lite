# HuskyLens 2 MakeCode 擴充（課堂精簡版）

本儲存庫修改自 DFRobot 官方擴充 [pxt-DFRobot_HuskyLensV2](https://github.com/DFRobot/pxt-DFRobot_HuskyLensV2)（MIT 授權，版權歸 DFRobot 所有），供屏科大幼保系「程式教育機器人」課程使用。

- **v1.1.7**：官方 v1.1.7 原版，未修改。
- **v1.1.8**：以 v1.1.7 為基礎，只把課程用不到的積木和演算法選項設為隱藏，程式碼沒有刪改。保留：初始化、切換演算法、學習／忘記 ID、人臉辨識、物體辨識、物體追蹤、顏色辨識、巡線、標籤辨識。
- **v1.1.9**：再開放「自學習分類」「手勢辨識」「姿態辨識」「表情辨識」，供期末專題使用（自己教鏡頭認東西、猜拳、律動、情緒教育）。

為什麼不用官方最新版：官方 V1.2.0（2026-11-23）對應鏡頭韌體 1.4.2 以後，接收緩衝區加大，在 micro:bit V1.5 上會記憶體不足（錯誤 021）。本課程鏡頭韌體為 1.2.2，維持 v1.1.x。

---

# HuskyLens 2

[HUSKYLENS 2 is an easy-to-play AI vision sensor that provides a variety of AI vision functions, such as object detection, pose recognition, and instance segmentation.](https://www.dfrobot.com/product-2995.html)
## Basic usage

## Example
HuskyLens 2 offers a very detailed tutorial on using MakeCode.(https://wiki.dfrobot.com/Tutorial%20for%20HUSKYLENS%202%20and%20micro:bit%20Graphical%20Programming(MakeCode))

* HuskyLens 2 Init I2C and select pattern.

```blocks
    huskylens2.I2CInit()
    huskylens2.switchAlgorithm(huskylens2.Algorithm.AlgorithmFaceRecognition)

```

* HuskyLens 2 collects data for facial recognition and outputs it.

```blocks
    basic.forever(function () {
        huskylens2.getResultFaceRecognition()
        if (huskylens2.availableFaceRecognition()) {
            serial.writeLine("Id:" + huskylens2.cachedCenterResult(huskylens2.BasePropertyId.Id))
            serial.writeLine("NAME:" + huskylens2.cachedCenterResult(huskylens2.BasePropertyId.Name))
            serial.writeLine("X:" + huskylens2.cachedCenterResult(huskylens2.BasePropertyId.XCenter))
            serial.writeLine("Y:" + huskylens2.cachedCenterResult(huskylens2.BasePropertyId.YCenter))
            serial.writeLine("W:" + huskylens2.cachedCenterResult(huskylens2.BasePropertyId.Width))
            serial.writeLine("H:" + huskylens2.cachedCenterResult(huskylens2.BasePropertyId.Height))
            serial.writeLine("----")
        }
    })

```


## License

MIT

Copyright (c) 2020, microbit/micropython Chinese community  

## Supported targets

* for PXT/microbit