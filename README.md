主要目標是測試不同檔案格式對 YOLOv5 模型在偵測準確度和延遲方面的影響，並探討修改邊界框損失計算方法對 YOLOv5 損失函數的影響。
報告的主要發現：

●  目標 A：測試相同 YOLOv5 模型在不同檔案格式下的表現
  ○  硬體環境為RTX4060 + Ryzen™ 9 8945HS，作業系統為WSL2 (Ubuntu 24.04.1 LTS)
  ○  在 GPU 測試中，TensorRT 引擎格式表現最佳，在所有格式中延遲最低。
  ○  令人驚訝的是，在 CPU 測試中，ONNX 格式是最有效的選擇。
  ○  模型大小分析顯示，INT8 量化實現了最小的檔案大小，但這並沒有轉化為預期的 CPU 性能提升(高延遲率，可能與網路架構相關)。
  ○  對於 GPU 部署，TensorRT 顯然是最佳選擇。
  ○  對於 CPU 部署，ONNX 提供了性能和準確性的最佳平衡。

●  目標 B：觀察修改 YOLOv5 損失函數中邊界框損失計算方法的影響
  ○  實驗結果表明，預設的 CIoU 損失指標提供了最佳的整體性能，在 mAP50 和 mAP50:95 中取得了最高分數，以及顯著的精度和召回率值。
  ○  儘管理論上，提出的 IIoU 和 EIoU 指標預計會超過 CIoU，但它們的實驗性能分別排名第四和第五。
  ○  未來的工作可能會探索物件損失和位置損失（邊界框損失）之間的關係。總之，這項研究為資源受限平台上的跌倒偵測系統部署提供了實用的見解，突出了在模型優化決策中經驗測試比理論假設的重要性。

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The main objective is to test the impact of different file formats on YOLOv5 model's detection accuracy and latency, and to explore the effects of modifying bounding box loss calculation methods on YOLOv5 loss function.
Key findings of the report:

●  Objective A: Testing the performance of the same YOLOv5 model across different file formats
  ○  Hardware environment: RTX4060 + Ryzen™ 9 8945HS, operating system: WSL2 (Ubuntu 24.04.1 LTS)
  ○  In GPU testing, TensorRT engine format performed best, showing the lowest latency among all formats.
  ○  Surprisingly, in CPU testing, ONNX format emerged as the most efficient choice.
  ○  Model size analysis revealed that INT8 quantization achieved the smallest file size, but this didn't translate to expected CPU performance improvements (high latency rates, possibly architecture-related).
  ○  For GPU deployment, TensorRT is clearly the optimal choice.
  ○  For CPU deployment, ONNX provides the best balance of performance and accuracy.

●  Objective B: Observing the effects of modifying bounding box loss calculation methods in YOLOv5 loss function
  ○  Experimental results showed that the default CIoU loss metric provided the best overall performance, achieving the highest scores in both mAP50 and mAP50:95, along with significant precision and recall values.
  ○  Although theoretically, the proposed IIoU and EIoU metrics were expected to outperform CIoU, they ranked fourth and fifth respectively in experimental performance.
  ○  Future work might explore the relationship between object loss and localization loss (bounding box loss). 
     In conclusion, this study provides practical insights for deploying fall detection systems on resource-constrained platforms, 
     highlighting the importance of empirical testing over theoretical assumptions in model optimization decisions.
