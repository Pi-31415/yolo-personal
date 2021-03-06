<p>
This is a personal implementation of YOLO v5 by Pi.
</p>

Dataset : https://drive.google.com/file/d/11q37nAXEVgagxyj2LjgkXfc2LzNqNbmo/view?usp=sharing

Python >= 3.6.0 required with all [requirements.txt](https://github.com/ultralytics/yolov5/blob/master/requirements.txt) dependencies installed:

To test the repository, run these commands first.

```bash
$ git clone https://github.com/Pi-31415/yolo-personal
$ sudo apt install python3-pip
$ sudo -H pip3 install --upgrade pip
$ sudo -H pip2 install --upgrade pip
$ cd yolo-personal
$ pip3 install -r requirements.txt
```

Then, place the image you want to test into the yolov5 folder. In this case, it is called 3.png.

Then run the detect command.

```
$ python3 detect.py --weights runs/train/exp10/weights/last.pt --img 640 --conf 0.25 --source 'a.png'
```

Note : 5 = first train
       7 = with new ojects
       10 = latest train

The result will be in runs/detect/exp (read the terminal output for exact location)


To train the model, train with
```
python3 train.py --img 640 --batch 16 --epochs 2500 --data sciroc.yaml --weights yolov5s.pt --cache --nosave
```

To get images from ros node, run

```
rosrun image_view image_saver image:="/xtion/rgb/image_rect_color"
```

To copy exchange folder contents to the docker, run
```
cp ../exchange/* ./
```

To run simulation, run

```
roslaunch tiago_998_gazebo tiago_navigation.launch
```


# Notes

- There are some warnings (WARNING: Value for scheme.headers does not match.) when installing required python packages, but does not affect the simulation at all.
- torch>=1.7.0 (831.4 MB) will take a while to download everytime docker container is started.
