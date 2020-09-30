[![HitCount](http://hits.dwyl.com/jordandarbyshire/amenity_detection.svg)](http://hits.dwyl.com/jordandarbyshire/amenity_detection)

# Using Object Detection to Classify Amenities in Vacation Rental Listings
### Use of CNNs and transfer learning to detect objects in images

![Optional Text](../master/images/project_overview.PNG)

**Notebooks:**

| Item |      Notebook     |    Environment    |
|:----:|:-----------------:|:-----------------:|
|   1  | amenity_detection | Base + Tensorflow |

**Libraries:**
* Numpy
* Pandas
* OpenCV
* Matplotlib
* TensorFlow
* Keras

## **Project Overview**
### Inspiration
The inspiration for this project comes from a [Medium article](https://medium.com/airbnb-engineering/amenity-detection-and-beyond-new-frontiers-of-computer-vision-at-airbnb-144a4441b72e) that highlighted an Airbnb computer vision project where they aimed to detect room type by the types of objects identified in their listing photos. Airbnb's motivation was to uphold high quality listings on their site.

I wanted to do this project because of my interest in the Computer Vision field, which is still rapidly evolving. I also have a love for traveling and have had a lot of experience using these rental sites. 

### Motivation
The purpose of this project is to identify objects from images of homes uploaded onto vacation rental sites. Potential customers browsing vacation rental sites are looking for specific amenities in their vacation rental. For example, they want an oven to cook in, a pool to swim in, a pool table for entertainment... the list goes on. When a property owner creates an ad on a vacation rental website, they would usually manually type in their amenities or select from a large list. Inaccurate amenities can result in lost revenue due to bad reviews or last-minute cancellations.

Users of the website will search for properties based on their desired amenities and will be shown a list of properties based on their preferences. What if there was an easier way to add amenities to the listing, simply by uploading the property images without the manual labor? This is where Object Detection comes in.

### Potential Applications
Any hotel or vacation rental site such as Airbnb, Vrbo, Hotels.com, TripAdvisor, etc.

## Dataset
The dataset I used for this project is [Open Images V4](https://storage.googleapis.com/openimages/web/factsfigures_v4.html), which contains 9 million images spanning 600 classes. It is the largest existing dataset with object location annotations, which are bounding boxes drawn by humans to ensure accuracy and consistency. The images often show complex scenes with several objects (8 annotated objects per image on average).

I chose this dataset due to the number of classes applicable to the business problem. The inclusion of the bounding box "labels" was also a bonus. I chose the most relevant 20 classes based on amenities that would be desirable to the consumer such as swimming pool, televison, dining room table, fireplace, bathtub.

### Building the Custom Dataset
The biggest challenge with starting an Object Detection project is putting together a custom dataset to run models. Since the Open Images dataset is so massive, it would be a monumental task to download the full dataset (over 0.5 TB in size) and pick through the data to get what I needed. The Open Images website does not provide an option to download select classes of images. Fortunately, I discovered that there are a few open source solutions to this problem. I ended up using the [OIDv4 Toolkit](https://github.com/EscVM/OIDv4_ToolKit) to download the desired image classes.

## Modeling
This project made use of pre-trained models for object detection. The benefit is to leverage features and weights from previously trained models, which are trained on similar datasets. In the case of computer vision, low-level features such as edges, shapes, corners and intensity can be shared among tasks (transfer learning).

| Pre-trained model |   Feature extractor  |                        Pros                        |                      Cons                     |
|:-----------------:|:--------------------:|:--------------------------------------------------:|:---------------------------------------------:|
|  SSD MobileNet V2 |      VGG16 (FPN)     | Works well on large objects                        | Doesn't fare well on small objects            |
|     RetinaNet     |    ResNet50 (FPN)    | Works well on multiple scales | None                                          |
|       YOLOv3      | Darknet53 (FPN-like) | Very fast, works well on small objects             | Doesn't fare well on medium and large objects |

## Results
The RetinaNet model performed a little better than SSD MobileNet with an estimated accuracy score of 35% (versus 30%). While not as high as my initial expectations, if you consider the complexity of my dataset (15 classes, multiple classes in each image, objects of all scales) then this score is acceptable for my project.

![Optional Text](../master/images/model_results.PNG)

Obviously, in order for this project to be run successfully on a vacation rental website the accuracy needs to be improved considerably.

## Future Steps
I would like to get the YOLOv3 system up and running for real-time detection on
videos rather than images. I think this would be a really neat feature for a vacation rental site to have, where a user could simply walk around their property with a cell phone in hand, and a list of amenities could be generated.