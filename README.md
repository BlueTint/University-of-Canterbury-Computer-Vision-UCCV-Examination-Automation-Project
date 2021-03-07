# University-of-Canterbury-Computer-Vision-UCCV-Examination-Automation-Project
UCCV School of Mathematics &amp; Engineering 2020-2021 Project - Using Computer Vision and Deep Learning to automate examinations processing

Educational Institutions have a core reliance on the practice of
examinations for student performance assessment. As
technological advancements continue to be a pervasive force in
the improvement of education at a wide scope, the process of
data ingestion of handwritten examinations continues to remain
a process of manual human data interpretation and entry.
The application of deep learning and computer vision tools and
methodologies can be employed to automate this process to
reach an accuracy that can mimic human-level error. 

This project serves a long-standing need for the University of Canterbury School of Engineering. The
UC school of engineering offers a diverse range of academic courses throughout each academic year,
with students partaking in multiple papers every term, semester and academic year. The UC engineering
school itself, as part of the greater UC institution, accounts for a large portion of the UC academic
institution itself in terms of the student body population. The project originates from the biannual (in
some cases, more frequent) course examinations that are undertaken which traditionally sees a heavily
paper-based, in-person, supervised method. While much of the examinations processing methodology
which aims to get the completed exams from the exam script to a finalised grade that is available to
students online has remained the same and may remain the same for some time to come; a particular
step within the examinations processing pipeline has been identified as having the potential to be
markedly improved upon using automation efficiency.

![CNN](https://user-images.githubusercontent.com/45345672/110233533-71b70900-7f89-11eb-8eed-c1f687452675.PNG)

Convolutional neural network model for handwritten characters (1 of 2)

Convolutional neural network models trained using NIST Special Database 19, Extended MNIST (EMNIST) data which 
consists of class balanced Handwritten digit and English alphabetical character datasets collected from 
employees of American Census Bureau.

![EMNIST](https://user-images.githubusercontent.com/45345672/110233591-be024900-7f89-11eb-9ecb-9743001ba30d.PNG)

EMNIST Letter and Digit dataset

![CNN Digit](https://user-images.githubusercontent.com/45345672/110233831-9b712f80-7f8b-11eb-9c2d-a6fa189421e9.png)

Snippet of CNN training & Validation curve behaviour

Open Source Computer Vision Library (OpenCV) was selected as the library of choice due to its mature 
platform and extensive library of computer vision functions and algorithms.

The approach that is taken in order to identify, extract and process the examination forms is approached 
in a systematic manner that is fashioned into a pipeline of techniques which are slowly constrained in 
order to isolate each feature of interest and their digit or alphabetical contents. The first challenge that 
must be put in consideration when architecting the object detection pipeline derives from the nature of 
the examinations forms themselves. The problem statement consists of eight unique examinations form 
templates upon which information is to be extracted, the stylistic differences between the forms are 
varying in terms of their degree of similarity and dissimilarity from one another. 

![contours](https://user-images.githubusercontent.com/45345672/110233659-2d783880-7f8a-11eb-9bad-5b892dfbe4b1.gif)
Contour Extraction using OpenCV

The processed contours undergo a final filtering which is done to separate the digit classes from the 
letter classes. These digit and letter class characters will invariably come in different sizes, owing to the 
template type. The width and height thresholds for the digits and letters were found to exist within the 
following dimension constraints.

The character prediction approach taken will differ between digit prediction and letter prediction, this 
is due to the disparity in model performance that was achieved between the digit and letter models 
trained using the convolutional neural network technique. The two-model approach addresses the ability 
to garner a higher predictive accuracy on characters by allowing each model to specialize on their digit 
or letter characters. However, the disparity in model accuracy occurs due to the difference in complexity 
of the data between the digit data which has only 10 classes, this is in comparison to the letter model 
which contains 26 classes - further complicated by the combination of capitalised and lower-case 
versions of each letter appearing under the same class label. 

![output](https://user-images.githubusercontent.com/45345672/110233760-1a199d00-7f8b-11eb-833e-630536915b10.PNG)

With a digit model accuracy of 99.80% and a letter accuracy between 91.60% - 92.45%, the prediction 
approach taken is to allow the digit model to predict over all digit instances of student ID, total mark 
and question/section marks due to its strong predictive accuracy, alongside the importance of retrieving 
a complete numerical student ID and total mark (mission critical features). 

The student credentials matching system is based upon objective three which places the need to develop 
a method that uses both the predicted student ID digit string and student initial/s in order to match the 
examination script to the corresponding student that is recorded in the school departments student 
register database based on the same credentials present in the database. 

The credentials matching methodology of a sliding window and point system is used to allow for the correct matching 
to occur, despite these instances. The sliding window matching method operates by first identifying and 
comparing the OCR predicted ID string length (character count) to the string length in the student ID 
column of the database (dataframe).

![scan](https://user-images.githubusercontent.com/45345672/110233780-47664b00-7f8b-11eb-8b51-c8c6d2e7e258.PNG)

Results
![Results](https://user-images.githubusercontent.com/45345672/110233800-6664dd00-7f8b-11eb-8399-28bf8b0fa535.PNG)
Resulting output dataframe (blurred for privacy) alongside system performance against a test run of examination data



