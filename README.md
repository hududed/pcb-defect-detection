# pcb-defect-detection

## Data load
1. Get `PCB_DATASET` from https://www.kaggle.com/datasets/akhatova/pcb-defects?resource=download
## Data clean
2. Get the class names from the XML files. You can clone this `https://github.com/isabek/XmlToTxt`
E.g. In `PCB_dataset/Annotations/Missing_hole/01_missing_hole_08.xml` you will find the class name `<name>missing_hole</name>`.  
In `XmlToTxt`, add `missing_hole` to `classes.txt`.
3. Repeat for all classes.
4. In `XmlToTxt`, have empty folders `out` and `xml`, and convert xml to txt with `python xmltotxt.py -c cls.txt -xml xml -out out`.  
5. Move all output folders from `XmlToTxt/out` to `PCB_DATASET/Annotations`.
6. You can remove `XmlToTxt` if you wish.
7. Create the following structure in `root` project folder `pcb-defect-detection`:
```
    - dataset
      -- images
        --- train
        --- val
      -- labels
        --- train
        --- val
```
8. Merge images from `PCB_DATASET/images` to `PCB_DATASET/Annotations`.
9. Move `Annotations` to `root` project folder.
10. Organize the images and labels for training/validation e.g. `python -c "from utils import to_v5_directories; to_v5_directories("dataset/images/train","dataset/images/val","dataset/labels/train","dataset/labels/val", "Annotations/Missing_hole")`

## Results

See [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Ky4JscDhzus5mhT_hxh7HZt4Fwa44nNe#scrollTo=OeS2TL-sjmD3)