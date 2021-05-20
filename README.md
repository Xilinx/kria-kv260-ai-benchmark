<table class="sphinxhide">
 <tr>
   <td align="center"><img src="https://www.xilinx.com/content/dam/xilinx/imgs/press/media-kits/corporate/xilinx-logo.png" width="30%"/><h1>Kria&trade; KV260 Vision AI Starter Kit Benchmark </h1>
   </td>
 </tr>
</table>

# Instructions
This repo will run following Benchmarks:  
* Inception V4 : 299x299
* VGG-19 : 224x224
* Tiny Yolo V3 : 416x416
* ResNet-50 : 224x224
* SSD Mobilenet-V1 : 300x300
* SSD ResNet34 : 1200x1200

## Directory Structure Introduction

```
kria-kv260-ai-benchmark
	├── benchmark-application
	│   ├── build.sh
	│   ├── src
	│   │   └── test_dpu_runner_mt.cpp
	│   └── test_dpu_runner_mt
	├── models
	│   ├── b3136
	│   │   ├── inception_v4
	│   │   ├── mlperf_ssd_resnet34_tf
	│   │   ├── resnet50
	│   │   ├── ssd_mobilenet_v1_voc_tf
	│   │   ├── tiny_yolov3
	│   │   └── vgg_19_tf
	│   └── b4096
	│       ├── inception_v4
	│       ├── mlperf_ssd_resnet34_tf
	│       ├── resnet50
	│       ├── ssd_mobilenet_v1_voc_tf
	│       ├── tiny_yolov3
	│       └── vgg_19_tf
	└── README.md
```

# Set up instructions
```
git clone https://gitenterprise.xilinx.com/aisw/kria-kv260-ai-benchmark.git
```
## Download models
```
cd kria-kv260-ai-benchmark/benchmark-application
wget https://www.xilinx.com/bin/public/openDownload?filename=kv260-benchmark-models.tar.gz -O kv260-benchmark-models.tar.gz
tar -xzvf kv260-benchmark-models.tar.gz
```

# Running Benchmarks

## Running Individual Benchmark Model

The following command is to run the `Resnet50` model in 1 thread.
```
env SLEEP_MS=180000 ./test_dpu_runner_mt ../models/b3136/resnet50/resnet50.xmodel k_0 1
```
The following command is to run the `Resnet50` model in 2 thread.
```
env SLEEP_MS=180000 ./test_dpu_runner_mt ../models/b3136/resnet50/resnet50.xmodel k_0 2
```


 <summary><b> Parameter about the abovecommand </b></summary>
 
| No\. | Parameter                  | Comment                                                      |
| :--- | :----------------------- | :----------------------------------------------------------- |
| 1    | env SLEEP_MS=180000        | test for 180 seconds                              |
| 2    | test_dpu_runner_mt         | test program                              |
| 3    | ../models/b3136/resnet50/resnet50.xmodel  | test model, it should be <model>.xmodel                 |
| 4    | k_0                        | kernel number, _0 means the first kernel            |
| 5    | 1                          | thread number, 1 means run in 1 thread, 2 means run in 2 threads        |


Note that the default DPU integrated in SoM is B3136. Please use the corresponding model to do the benchmark.

