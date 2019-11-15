# Focal Loss for Dense Rotation Object Detection

## Performance
### DOTA1.0
| Model |    Backbone    |    Training data    |    Val data    |    mAP   | Model Link | Anchor | Reg. Loss| Angle Range | lr schd | Data Augmentation | GPU | Image/GPU | Configs |      
|:------------:|:------------:|:------------:|:---------:|:-----------:|:----------:|:-----------:|:-----------:|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|    
| RetinaNet (baseline) | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 53.17 | - | H | smooth L1 | 90 | 1x | No | 8X GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v3.py |    
| RetinaNet (baseline) | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 63.18 | [model](https://drive.google.com/file/d/18Z3NWhL4gQB5yJLCXBcHBnK-6BPle3m1/view?usp=sharing) | H | smooth L1 | 90 | 1x | No |**1X** GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v4.py |     
| RetinaNet (baseline) | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 62.79 | - | H | smooth L1 | 90 | **2x** | No | 8X GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v8.py |     
| RetinaNet (baseline) | **ResNet101_v1** 600->800 | DOTA1.0 trainval | DOTA1.0 test | 64.73 | [model](https://drive.google.com/file/d/16XCbS9T-tTr7ySa-qlyc8TuufAxJTvD4/view?usp=sharing) | H | smooth L1 | 90 | 1x | No | 1X GeForce RTX 2080 Ti | 1 | cfgs_res101_dota_v9.py |   
| RetinaNet (baseline) | **ResNet152_v1** 600->800 | DOTA1.0 trainval | DOTA1.0 test | 65.79 | - | H | smooth L1 | 90 | 1x | No | 1X GeForce RTX 2080 Ti | 1 | cfgs_res152_dota_v12.py |
| RetinaNet | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 65.11 | [model](https://drive.google.com/file/d/1vnJd4FEvy61yvcYqhZJgfnxJ3fByULOR/view?usp=sharing) | H | smooth L1 + **atan(theta)** | 90 | 1x | No | 1X GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v16.py |     
| RetinaNet | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 64.10 | [model](https://drive.google.com/file/d/1SgiDME_gHzKrFxoZSjS9E-_QbGiBr9lV/view?usp=sharing) | H | smooth L1 | **180** | 1x | No | 1X GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v15.py |     
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| RetinaNet (baseline) | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 61.94 | - | R | smooth L1 | 90 | 1x | No | 1X GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v1.py |
| RetinaNet (baseline) | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 62.25 | - | R | smooth L1 | 90 | **2x** | No | **8X** GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v10.py |
| RetinaNet | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 62.69 | - | R | **iou-smooth L1** | 90 | 1x | No | 1X GeForce RTX 2080 Ti | 1 | cfgs_res50_dota_v5.py |    
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| [R<sup>3</sup>Det](https://github.com/SJTU-Det/R3Det_Tensorflow) | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 66.31 | -  | H + R | smooth L1 | 90 | 2x | No | 4X GeForce RTX 2080 Ti | 1 | - |
| [R<sup>3</sup>Det*](https://github.com/SJTU-Det/R3Det_Tensorflow) | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 67.20 | -  | H + R | smooth L1 | 90 | 2x | No | 8X GeForce RTX 2080 Ti | 1 | - |
| [R<sup>3</sup>Det](https://github.com/SJTU-Det/R3Det_Tensorflow) | **ResNet101_v1** 600->800 | DOTA1.0 trainval | DOTA1.0 test | 71.69 | -  | H + R | smooth L1 | 90 | 3x | Yes | 8X GeForce RTX 2080 Ti | 1 | - |
| [R<sup>3</sup>Det](https://github.com/SJTU-Det/R3Det_Tensorflow) | **ResNet152_v1** 600->800 | DOTA1.0 trainval | DOTA1.0 test | 72.81 | -  | H + R | smooth L1 | 90 | **4x** | Yes | 8X GeForce RTX 2080 Ti | 1 | - |
| [R<sup>3</sup>Det*](https://github.com/SJTU-Det/R3Det_Tensorflow) | **ResNet152_v1** 600->800 | DOTA1.0 trainval | DOTA1.0 test | 73.74 | -  | H + R | smooth L1 | 90 | **4x** | Yes | 8X GeForce RTX 2080 Ti | 1 | - |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| **R<sup>3</sup>Det++** | ResNet50_v1 600->800 | DOTA1.0 trainval | DOTA1.0 test | 68.54 | -  | H + R | smooth L1 | 90 | 2x | No | 8X GeForce RTX 2080 Ti | 1 | - |
| R<sup>3</sup>Det++ | **ResNet152_v1** 600->800 | DOTA1.0 trainval | DOTA1.0 test | 74.41 | -  | H + R | smooth L1 | 90 | 4x | Yes | 8X GeForce RTX 2080 Ti | 1 | - |
| R<sup>3</sup>Det++ | ResNet152_v1 **MS** | DOTA1.0 trainval | DOTA1.0 test | 76.56 | - | H + R + more | smooth L1 | 90 | 6x | Yes | 4X GeForce RTX 2080 Ti | 1 | - |

[R<sup>3</sup>Det*](https://github.com/SJTU-Det/R3Det_Tensorflow): R<sup>3</sup>Det with two refinement stages       
**Some model results are slightly higher than in the paper due to retraining.**