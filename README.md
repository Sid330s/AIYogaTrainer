
# AI Yoga Trainer: Real-Time Yoga Pose Feedback Using AI

![Yoga Trainer Logo](https://github.com/Sid330s/AIYogaTrainer/blob/main/imgs/favicon-16x16.png)  

[**Open AI Yoga Trainer App**](https://sid330s.github.io/AIYogaTrainer)  

**Authors**: Siddharth Kale, Prashil Jambhulkar, Sampatlal Jangid, Vedant Mahajan, Ganesh Bhuthkar  

**Affiliation**: Vishwakarma Institute of Technology, Pune, India  

### Abstract

In today’s fast-paced world, it’s challenging to find time for physical activities like Yoga. Moreover, many individuals lack expert guidance, which leads to improper execution of Yoga poses. To address this, we propose a solution that utilizes **Machine Learning (ML)** and **Computer Vision (CV)** to provide real-time feedback on Yoga poses. By leveraging the **OpenPose** library, our system estimates the user's body pose and compares it with expert poses, offering feedback on pose accuracy using metrics like **Cosine Similarity**.

#### Keywords

Machine Learning, Computer Vision, OpenPose, Artificial Intelligence, Yoga, Pose Estimation


### 1. Introduction

Our daily routines are often busy, leaving little room for physical exercises like Yoga. Despite its health benefits, practicing Yoga is often neglected due to time constraints or the lack of proper guidance. Performing Yoga poses incorrectly can also lead to injuries or reduced effectiveness.

To solve this, we propose an AI-powered Yoga Trainer that leverages computer vision and machine learning to guide users in performing Yoga poses accurately. By using **OpenPose**, a state-of-the-art real-time multi-person pose detection system, our app estimates the user's body posture and compares it with expert poses. The feedback provided helps users improve their poses for better practice and safety.

#### Example: **Surya Namaskar (Sun Salutation)**

Performing **Surya Namaskar** for just 20-30 minutes can offer the benefits of over 250 Yoga poses, burning about 417 calories. This demonstrates how effective even a short Yoga session can be.

---

### 2. OpenPose and Cosine Similarity

**OpenPose** is a real-time system that detects human body, hand, face, and foot keypoints (135 keypoints in total). It uses a multi-branch, multi-stage **Convolutional Neural Network (CNN)** to accurately estimate a person’s pose.

**Cosine Similarity** is used to compare the user's pose to expert poses. It measures the angle between two vectors (poses), allowing us to determine the degree of similarity between them. The smaller the angle between the vectors, the more similar the poses.

#### Cosine Similarity Formula:

```
similarity(A, B) = (A ⋅ B) / (||A|| * ||B||)
```


Where:
- **A** and **B** are pose vectors.
- **A ⋅ B** is the dot product of the vectors.
- **||A||** and **||B||** are the magnitudes (lengths) of the vectors.


### 3. Working Principle

#### Step 1: Pose Estimation
The system captures a stream of 2D body coordinates from the user’s current frame using **OpenPose**. The keypoints for each body part (e.g., shoulders, elbows, knees, ankles) are then extracted.

#### Step 2: Filter and Validate Keypoints
After detecting the keypoints, the system filters out any irrelevant ones and keeps only the necessary keypoints. Each keypoint comes with a confidence score, and only those with a score above a certain threshold are used for further calculations.

Example keypoint data:

```json
"keypoints": [
  {"part": "leftAnkle", "position": {"x": 233.76, "y": 326.54}, "score": 0.91},
  {"part": "leftElbow", "position": {"x": 258.69, "y": 136.89}, "score": 0.97},
  {"part": "leftKnee", "position": {"x": 225.52, "y": 257.22}, "score": 0.99}
]
```

#### Step 3: Angle Calculation
The system computes angles between the detected keypoints to assess whether the user’s pose matches the correct pose. For example, it calculates the angle between the shoulder, elbow, and wrist to check for proper alignment.

#### Step 4: Feedback Generation
The system compares the user’s pose with expert poses using **Cosine Similarity**. If the similarity score is high, the pose is considered correct. If not, feedback is provided to the user to adjust their posture accordingly.


### 4. Conclusion

This system combines **Machine Learning** and **Computer Vision** to provide real-time feedback on Yoga poses. By using **OpenPose** for pose estimation and **Cosine Similarity** for comparison, users can receive accurate guidance on performing Yoga poses correctly, even without a physical instructor. This approach makes Yoga practice more accessible, safer, and effective.


### 5. Future Work

- **Improved Feedback Mechanisms**: Incorporating more detailed and personalized feedback based on user performance.
- **Integration with Wearable Devices**: Using sensors to further enhance pose accuracy and provide real-time adjustments.
- **Voice Guidance**: Adding audio feedback to guide users through their practice more interactively.

---

### 6. Acknowledgments

We would like to thank the **Vishwakarma Institute of Technology**, Pune, for supporting this project. Additionally, special thanks to the developers of the **OpenPose** library for providing a powerful tool for pose estimation.

---

### 7. References

1. OpenPose: https://github.com/CMU-Perceptual-Computing-Lab/openpose
2. Cosine Similarity: https://en.wikipedia.org/wiki/Cosine_similarity