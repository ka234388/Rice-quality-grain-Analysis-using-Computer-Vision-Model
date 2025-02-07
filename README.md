# Rice-quality-grain-Analysis-using-Computer-Vision-Model
### Rice Quality Assessment Using Image Processing

#### Overview

This project focuses on simplifying the evaluation of rice grain quality through image processing techniques. By examining the size and shape of rice grains, it replaces traditional, time-consuming methods with a faster, more reliable solution. Using high-resolution images, the system measures grain dimensions and categorizes them into industry-standard classifications such as Slender, Medium, Bold, and Round.

---

#### Summary

Assessing the quality of rice grains has always been a critical task in agriculture and food industries. However, conventional methods tend to be slow, costly, and heavily reliant on manual labor. This project introduces a solution that leverages image processing to streamline the process. Instead of relying on trained models or labeled datasets, it uses straightforward, rule-based logic to analyze the physical properties of rice grains. The system works consistently across various datasets, including user-provided images, and delivers dependable results.

---

#### Key Features
- **Preprocessing:** The system cleans up noise from images and isolates grains for better analysis.
- **Edge Detection:** Clear grain outlines are captured for accurate measurements.
- **Measurement:** Each grain's dimensions are calculated, focusing on its length-to-width ratio.
- **Classification:** Grains are sorted into categories (Slender, Medium, Bold, Round) based on their ratios.
- **Adaptability:** Users can analyze custom datasets with minimal setup.

---

#### Dataset Information

This system is built using the **Rice Image Dataset**, which can be downloaded from Kaggle:  
[**Rice Image Dataset on Kaggle**](https://www.kaggle.com/datasets/muratkokludataset/rice-image-dataset?resource=download)

The dataset includes high-resolution images taken against a black background, making it easy to isolate individual grains. The system also supports user-generated datasets. To prepare custom data, users should capture images under good lighting conditions and ensure the grains are placed on a plain, dark surface for compatibility with the system.

---

#### How to Use the System

##### 1. **Download the Dataset**
Visit the Kaggle dataset link above and download the `archive.zip` file to your local device.

##### 2. **Upload the File to Colab**
Upload the `archive.zip` file to your Colab environment by dragging it into the file manager.

##### 3. **Extract the Dataset**
Run this code to unzip the dataset in Colab:
```python
import zipfile

zip_path = "/content/archive.zip"  # Path to the uploaded ZIP file
extract_path = "/content/Rice_Image_Dataset"  # Where to extract the files

with zipfile.ZipFile(zip_path, 'r') as zip_ref:
    zip_ref.extractall(extract_path)
print("Dataset successfully extracted to:", extract_path)
```

##### 4. **Check the File Structure**
Make sure the images were extracted properly by listing the files:
```python
import os

dataset_folder = "/content/Rice_Image_Dataset"
for root, dirs, files in os.walk(dataset_folder):
    print("Directory:", root)
    print("Subdirectories:", dirs)
    print("Files:", files[:5])  # Show a preview of 5 files
```

##### 5. **Update Image Path in the Code**
For processing a specific image, adjust the `image_path` variable:
```python
image_path = "/content/Rice_Image_Dataset/Ipsala/Ipsala (1).jpg"
```

---

#### Example Outputs

Below are examples of the system's visual outputs at different processing stages:

1. **Classified as Bold**  
![image](https://github.com/user-attachments/assets/5a2df565-df9a-4cae-bad0-44d8f2e0a2dd)


2. **Classified as Round**  
![image](https://github.com/user-attachments/assets/dc0814b7-9e79-4695-ac8a-e73485fdb292)


3. **Classified as Medium**  
![image](https://github.com/user-attachments/assets/1ecbbce3-c3a2-46d5-9fd3-3fe8917990b4)

3. **Classified as Medium**  
   ![image](https://github.com/user-attachments/assets/1f6a9971-05ec-432a-89e6-c58c9c8021ff)


#### Process Breakdown

1. **Preprocessing**  
The image undergoes noise reduction and is converted to a binary format to clearly separate the grains from the background.

2. **Segmentation**  
Grains that are overlapping or touching are separated using erosion and dilation techniques. These steps ensure that each grain is measured individually without losing shape accuracy.

3. **Edge Detection**  
The system detects the edges of each grain using the Canny edge detection algorithm, producing clear outlines for measurement.

4. **Measurement**  
Grain dimensions are calculated, and the length-to-width (L/B) ratio is computed:
\[
\text{L/B Ratio} = \frac{\text{Length}}{\text{Width}}
\]

5. **Classification**  
Grains are classified into the following categories based on the L/B ratio:
   - **Slender:** L/B > 3
   - **Medium:** 2.1 ≤ L/B ≤ 3
   - **Bold:** 1.1 ≤ L/B < 2.1
   - **Round:** L/B ≤ 1

---

#### Example Results

```plaintext
Processing: /content/Rice_Image_Dataset/Ipsala/Ipsala (1).jpg
Class Counts: {'Slender': 10, 'Medium': 8, 'Bold': 7}

--- Results ---
Average Aspect Ratio: 2.45
Class Counts: {'Slender': 10, 'Medium': 8, 'Bold': 7}
```

---

#### Advantages and Limitations

**Strengths**
- **Speed:** Processes hundreds of grains in seconds, reducing labor and time.
- **Reliability:** Uses deterministic methods, ensuring consistent results.
- **Flexibility:** Handles both public datasets and user-provided data.

**Challenges**
- The system currently evaluates only physical traits like size and shape, leaving out chemical properties such as moisture or chalkiness.
- When grains are severely overlapped or lighting conditions are poor, segmentation accuracy may decrease.

---
- Designed measurement algorithms and classification logic.  
- Evaluated results and created visual outputs for analysis.

---

