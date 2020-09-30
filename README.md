# Using Object Detection to Classify Amenities in Vacation Rental Listings
### Use of CNNs and transfer learning to detect objects in images

![Optional Text](../master/images/project_overview.PNG)

**Notebooks:**

| Item |      Notebook     |    Environment    |
|:----:|:-----------------:|:-----------------:|
|   1  | amenity_detection | Base + Tensorflow |

## **Project Overview**
### Inspiration
The inspiration for this project comes from a [Medium article](https://medium.com/airbnb-engineering/amenity-detection-and-beyond-new-frontiers-of-computer-vision-at-airbnb-144a4441b72e) that highlighted an Airbnb computer vision project where they aimed to detect room type by the types of objects identified in their listing photos. Airbnb's motivation was to uphold high quality listings on their site.

I wanted to do this project because of my interest in the Computer Vision field, which is still rapidly evolving. I also have a love for traveling and have had a lot of experience using these rental sites. 

### Motivation
The purpose of this project is to identify objects from images of homes uploaded onto vacation rental sites. Potential customers browsing vacation rental sites are looking for specific amenities in their vacation rental. For example, they want an oven to cook in, a pool to swim in, a pool table for entertainment... the list goes on. When a property owner creates an ad on a vacation rental website, they would usually manually type in their amenities or select from a large list. Inaccurate amenities can result in lost revenue due to bad reviews or last-minute cancellations.

Users of the website will search for properties based on their desired amenities and will be shown a list of properties based on their preferences. What if there was an easier way to add amenities to the listing, simply by uploading the property images without the manual labor? This is where Object Detection comes in.

### Potential Applications
Any hotel or vacation rental site such as Airbnb, Vrbo, Hotels.com, TripAdvisor, etc.

### Dataset
The dataset I used for this project is [Open Images V4](https://storage.googleapis.com/openimages/web/factsfigures_v4.html), which contains 9 million images spanning 600 classes. It is the largest existing dataset with object location annotations, which are bounding boxes drawn by humans to ensure accuracy and consistency. The images often show complex scenes with several objects (8 annotated objects per image on average).

I chose this dataset due to the number of classes applicable to the business problem. The inclusion of the bounding box "labels" was also a bonus. I chose the most relevant 20 classes based on amenities that would be desirable to the consumer such as Swimming pool, Televison, Dining room table, fireplace, bathtub.