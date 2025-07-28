# Pool-Detection_Location-Mapping
# Swimming Pool Detection in Fort Wayne Using YOLO

This project demonstrates how to detect unmarked swimming pools in satellite imagery of Fort Wayne using YOLO-based object detection. The objective is to automate the detection and geolocation of swimming pools by scraping satellite images, annotating a dataset, training a YOLO model, and applying it to images of Fort Wayne.

![Detection Output](YOLO_obj_detection/output/images/sample_output.png)

## Problem Statement

Detect swimming pools in Fort Wayne using satellite images via:
- Scraping Google Maps imagery through Google Static Map API.
- Annotating data manually.
- Training a YOLOv8 model for object detection.
- Predicting coordinates of detected pools with bounding box areas.

---

## Technologies Used

- Python, OpenCV, Roboflow, YOLOv8, Google Maps API
- Platform: Google Colab, VSCode

## Constraints

- **API Limits**: Image scraping was limited by Google API quotas and budget constraints.
- **Manual Annotation**: 370+ images annotated using Roboflow.
- **Computational Power**: Model trained using Google Colab's free GPU, restricting model size and training time.

---

## Solution Workflow

### 1. Data Collection
- Scraped satellite imagery of cities (e.g., Atlanta, Chicago, Boston) using Google Static Map API.
- Extracted 5742 images for Fort Wayne separately for detection.

### 2. Data Annotation
- Annotated images using Roboflow.
- Augmented data (noise, flipping, brightness changes).
- Dataset split into:  
  `966 training` | `20 validation` | `15 test` images.

### 3. Model Training
- Trained YOLOv8 (nano, medium) and YOLOv11-nano.
- Final model: **YOLOv8-medium**
- Training Stats:
  - **mAP50**: 0.935
  - **Precision**: 0.849
  - **Recall**: 0.891

### 4. Pool Detection in Fort Wayne
- Applied model on scraped images.
- Saved results with:
  - Bounding box predictions
  - Latitude/longitude coordinates
  - Estimated area in m²

---

## Deliverables

| Component | Path |
|----------|------|
| YOLO Model (fine-tuned) | `YOLO_obj_detection/model` |
| Annotated Dataset | `YOLO_obj_detection/YOLO_train_test` |
| Fort Wayne Images | `YOLO_obj_detection/fort_wayne_images` |
| Prediction Outputs (Images) | `YOLO_obj_detection/output/images` |
| Final Output CSV | `YOLO_obj_detection/output/swimming_pool_location_and_area_meters.csv` |

---

## Results and Visualization

- Landmarks plotted manually in Google Maps using predicted coordinates.
- Dense and precise mapping confirmed many pools unlisted on Google Maps.

![Landmark Precision](YOLO_obj_detection/output/images/landmark_zoom.png)

---

## Future Scope

- Add more training examples of rooftop water tanks and lakes to reduce false positives.
- Use higher zoom factor (20+) for better resolution.
- Improve GPU availability for deeper training and larger datasets.

---


<!--
---

 ## 📚 References

- [Google Maps API Docs](https://developers.google.com/maps/documentation)
- [Roboflow](https://roboflow.com)
- [YOLO by Ultralytics](https://docs.ultralytics.com/tasks/detect/)
- [ArcGIS GeoAI Example](https://developers.arcgis.com/python/latest/samples/detecting-swimming-pools-using-satellite-image-and-deep-learning/)
- [AQUA Magazine](https://www.aquamagazine.com/builder/article/15279816/which-us-cities-have-the-most-homes-with-swimming-pools)

---
 ✅ -->

## Author
**Maleeha Sheikh**  
_Purdue University, Fall 2024 Machine Learning Project_
