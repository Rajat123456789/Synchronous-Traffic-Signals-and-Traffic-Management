# DeepLearningProject

Urban areas worldwide are plagued by
significant traffic congestion, leading to delays, high fuel
consumption, and increased emissions. Traditional traffic
management systems, being static and often
unresponsive to real-time conditions, further exacerbate
these issues. This project aims to address these challenges
by developing an innovative traffic management system
that leverages deep learning to dynamically synchronise
traffic signals based on real-time data. The primary
objective is to optimise traffic flow, reduce travel times,
and improve air quality, thereby promoting a sustainable
urban environment. By evaluating multiple datasets and
ultimately using GTA V for data collection, we were able
to tailor our data to specific project needs and simulate
precise traffic scenarios. While the implementation of
signal optimization is still in progress, we have
successfully collected the necessary data and established
methods for future data gathering. This report details
our methodology, data processing techniques, and the
framework for model training and testing, laying the
groundwork for a promising solution to modern traffic
management challenges.

Data Collection:
Camera Positioning: Virtual cameras were positioned at
key intersections to capture detailed traffic data,
including vehicle flow and signal timings.
Recording Traffic Data: We recorded traffic footage
from these strategic locations to collect data on vehicle
movements and traffic signal states.
Frame Extraction: Using OpenCV, we extracted frames
from the recorded videos at half-second intervals,
resulting in a dataset of 1450 frames.
4. Annotation and Data Processing (Rajat/Somesh):
Annotation:
- Tool Used: We used Roboflow for annotating the
extracted frames.
- Categories: Signals were categorised into three
classes: red, green, and yellow.
- Annotation Process: Each frame was carefully
annotated to identify and label traffic signals within
the scene. This resulted in a total of 1556
annotations across all frames


![image](https://github.com/user-attachments/assets/eb6b7f04-0b65-42ae-b362-fbd6aa447e8a)

![image](https://github.com/user-attachments/assets/2fe1d779-a006-45ba-888e-ac77d85c7725)

We removed 50% of
the frames containing red signal annotations to
address class imbalance. This reduced the dataset to
517 frames while maintaining a representative
sample of traffic signal states.



![image](https://github.com/user-attachments/assets/d79069cd-5496-419b-9d24-30ae44bd8292)
Here is a heatmap of the regions where the traffic
lights are detected.



Reasons for Choosing YOLOv8
- Speed and Accuracy: YOLOv8 maintains a robust
balance between detection speed and accuracy,
essential for real-time applications like traffic
signal detection. It can quickly process video
frames, identifying traffic signals with high
precision.
- Scalability: YOLOv8 offers various model sizes,
including YOLOv8n (nano), YOLOv8s (small),
YOLOv8m (medium), YOLOv8l (large), and
YOLOv8x (extra-large). This scalability enables us
to choose a model size that best fits our
computational resources and accuracy
requirements.

Model Training:
- Training Configuration: We configured the
YOLOv8m model with appropriate
hyperparameters, including a batch size of 4 and a
total of 30 epochs. This setup aimed to optimise the
model’s performance while ensuring efficient use
of computational resources.
Baseline Performance (Initial Model)
- Precision-Confidence Curve:
Green Signal: High precision with increasing
confidence.
Red Signal: Gradual increase in precision.
Yellow Signal: Lower precision overall.
All Classes: Achieves 1.00 precision at a
confidence level of 0.586.
- Precision-Recall Curve:
Green Signal: High precision (0.995) across recall
levels.
Red Signal: High precision (0.964) across recall
levels.
Yellow Signal: Very low precision (0.052).
All Classes: Mean Average Precision (mAP) at 0.5
is 0.670.
- Recall-Confidence Curve:
Green Signal: Higher recall with lower confidence.
Red Signal: Gradual decrease in recall with higher
confidence.
Yellow Signal: Very low recall.
All Classes: Recall of 0.98 at a confidence level of
0.000.
- Training and Validation Losses:
Train/Box Loss: Decreases steadily.
Train/Cls Loss: Decreases steadily.
Train/Dfl Loss: Decreases steadily.
Metrics/Precision (B): Fluctuates initially, then
stabilises.
Metrics/Recall (B): Fluctuates significantly, shows
improvement.
Metrics/mAP50 (B): Increases over epochs.
Metrics/mAP50-95 (B): Steady increase.
- Confusion Matrix:

![Screenshot 2024-09-12 at 5 37 00 PM](https://github.com/user-attachments/assets/b76bb4c5-8411-4c87-a2fa-0cbb357408c5)
![Screenshot 2024-09-12 at 5 37 10 PM](https://github.com/user-attachments/assets/eb0b1352-8207-4511-aaea-52984244e831)


![image](https://github.com/user-attachments/assets/99a96d14-0e64-4c85-b7ae-d5933056b9d8)
Final results





