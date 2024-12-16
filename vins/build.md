# Test VINS-MONO on EuRoC dataset

## How to build VINS-MONO?
To build VINS-MONO, you need install ROS first. See (http://www.ros.org/install/) for details.
We modify code to save vio trajectory for later evaluation. Note: trajectory logging is in a separated thread, so that estimator thread won't be blocked by logging.
Loop clousure are closed for fair comparison to other VIO algorithms.
```
## download code
cd ~/catkin_ws/src
git clone https://github.com/symao/VINS-Mono

## checkout to modify version which close viewer and loop closing
cd VINS-Mono
git checkout evaluation

## build
cd ~/catkin_ws
catkin_make
```

## How to run VINS-MONO on EuRoC datasets?
1. Download EuRoC dataset on https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets. NOTE: Download datasets in **rosbag(.bag)** rather than ASL Dataset Format(*.zip).
2. Batch run. Modify 'bag_dir' to your path which contains all rosbag file. And run 'python run_euroc.py'. It will run all rosbag files in bag_dir.

只开一个终端运行run_euroc.py，这个我在台式机上写了运行代码了，在run_euroc.py文件中我把 output_file 改为了 = '/home/huanhuan/.ros/vio.txt'，这样才没有出现mv的报错，输出在results文件夹中。而且我发现在Desktop文件夹中还会生成一个叫vins_result_no_loop.csv的csv文件，里面的数值初步推断是输出的txt文件四舍五入了一位得到的。
