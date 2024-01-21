### Prepare EmbodiedScan Data

1. Download ScanNet v2 data [HERE](https://github.com/ScanNet/ScanNet). Link or move the folder to this level of directory.

2. Download 3RScan data [HERE](https://github.com/WaldJohannaU/3RScan). Link or move the folder to this level of directory.

3. Download Matterport3D data [HERE](https://github.com/niessner/Matterport). Link or move the folder to this level of directory.

4. Download EmbodiedScan data and extract here.

The directory structure should be as below

```
data
├── scannet
│   ├── scans
│   │   ├── <scene_id>
│   │   ├── ...
├── 3rscan
│   ├── <scene_id>
│   ├── ...
├── matterport3d
│   ├── <scene_id>
│   ├── ...
├── embodied_occupancy
├── embodiedscan_infos_train_full.pkl
├── embodiedscan_infos_val_full.pkl
```

5. Enter the project root directory, extract images by running

```bash
python embodiedscan/converter/generate_image_scannet.py --dataset_folder data/scannet/
# generate_image_scannet.py can be very slow because it extracts images from .sens files. Add --fast to generate only images used by embodiedscan.
python embodiedscan/converter/generate_image_3rscan.py --dataset_folder data/3rscan/
```

The directory structure should be as below after that

```
data
├── scannet
│   ├── scans
│   │   ├── <scene_id>
│   │   ├── ...
│   ├── posed_images
│   │   ├── <scene_id>
│   │   |   ├── *.jpg
│   │   |   ├── *.png
│   │   ├── ...
├── 3rscan
│   ├── <scene_id>
│   │   ├── sequence
│   │   |   ├── *.color.jpg
│   │   |   ├── *.depth.pgm
│   ├── ...
├── matterport3d
│   ├── <scene_id>
│   ├── ...
├── embodied_occupancy
├── embodiedscan_infos_train_full.pkl
├── embodiedscan_infos_val_full.pkl
```

6. Put EmbodiedScan occupancy annotations by running

```bash
python embodiedscan/converter/put_occupancy_ann.py --src data/embodied_occupancy --dst data
```