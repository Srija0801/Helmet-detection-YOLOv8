\# Lightweight Helmet Detection Using Modified YOLOv8



\*\*An Experimental Study on the Safety Helmet Wearing Dataset (SHWD)\*\*



\## Project Overview



Developed a modified YOLOv8-based helmet detection system to investigate lightweight feature extraction, channel attention, alternative bounding-box regression loss, and high-resolution object detection.



The project evaluates four model configurations on the official Safety Helmet Wearing Dataset (SHWD), focusing on the trade-off between detection accuracy, model parameters, and computational complexity.



\## Key Contributions



\- Implemented \*\*LC\_CBS\*\*, a lightweight convolution block using feature gating and depthwise convolution for efficient feature extraction.

\- Integrated \*\*SE\_C2f\*\*, combining C2f feature extraction with Squeeze-and-Excitation channel attention.

\- Experimentally evaluated \*\*Wise-IoU (WIoU)\*\* as an alternative to CIoU for bounding-box regression.

\- Added a \*\*P2 high-resolution detection branch\*\* to improve small-object representation.

\- Converted Pascal VOC annotations into YOLO format and verified image-label correspondence across the official dataset splits.

\- Conducted controlled experiments and compared model performance using precision, recall, mAP, parameter count, and GFLOPs.



\## Architecture



The modified architecture combines LC\_CBS in selected backbone stages and SE\_C2f in the detection head. The P2 variant introduces an additional high-resolution detection scale alongside P3, P4, and P5.



\## Dataset



\*\*Safety Helmet Wearing Dataset (SHWD)\*\*



| Split | Images |

|---|---:|

| Training | 5,457 |

| Validation | 607 |

| Testing | 1,517 |

| Total | 7,581 |



Classes: `hat` and `person`.



\[Official SHWD Dataset](https://github.com/njvisionpower/Safety-Helmet-Wearing-Dataset)



\## Experimental Results



| Model | Parameters | GFLOPs | Precision | Recall | mAP@50 | mAP@50–95 |

|---|---:|---:|---:|---:|---:|---:|

| YOLOv8n + CIoU | 3.006M | 8.1 | 0.9200 | 0.8700 | 0.9240 | 0.5940 |

| Helmet Net + CIoU | 2.804M | 8.2 | 0.9134 | 0.8419 | 0.9048 | 0.5671 |

| Helmet Net + WIoU | 2.804M | 8.2 | 0.8886 | 0.8135 | 0.8760 | 0.5452 |

| Helmet Net + P2 + CIoU | 2.719M | 12.3 | 0.9131 | 0.8595 | 0.9208 | 0.5830 |



\## Key Findings



\- LC\_CBS and SE\_C2f-based Helmet Net reduced parameters by approximately \*\*6.73%\*\* compared with the YOLOv8n baseline.

\- The tested WIoU implementation did not improve detection performance.

\- Adding P2 improved mAP@50–95 from \*\*0.5671 to 0.5830\*\* compared with Helmet Net + CIoU.

\- P2 increased computational complexity from \*\*8.2 to 12.3 GFLOPs\*\*.

\- The original YOLOv8n baseline remained the strongest configuration on mAP@50–95.



\## Technologies Used



Python | PyTorch | Ultralytics YOLOv8 | OpenCV | NumPy | Matplotlib | Kaggle GPU



\## Project Documentation



\- Detailed project report: `report/`

\- Presentation: `presentation/`

\- Architecture diagram: `architecture/`

\- Experimental graphs: `results/`

\- Custom implementation: `implementation/`



\## Research Reference



Deng, L., Zhou, J., \& Liu, Q. (2024). \*Helmet Net: An Improved YOLOv8 Algorithm for Helmet Wearing Detection\*. International Journal of Networked and Distributed Computing, 12, 329–343.



\[https://doi.org/10.1007/s44227-024-00040-1](https://doi.org/10.1007/s44227-024-00040-1)

