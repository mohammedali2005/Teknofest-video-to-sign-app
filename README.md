# Sign Language Video-to-Avatar Pipeline

**Empowering Accessibility with AI: Automatic Sign Language Avatar Generation from Video**

## Overview

This project is a core component of our Teknofest submission, aiming to bridge the accessibility gap for the Deaf and Hard-of-Hearing community. We present a pipeline that automatically extracts sign language pose data from video, builds a searchable sign "dictionary," and animates a 2D avatar to visually represent sign language—paving the way for browser extensions and educational tools.

**Key Features:**
- **Pose Extraction:** Uses state-of-the-art pose estimation (MMPose/RTMPose) to extract 2D keypoints from sign language video clips.
- **Sign Dictionary:** Organizes extracted pose data into a searchable database, mapping ASL glosses to pose sequences.
- **2D Avatar Animation:** Animates a 2D character (with articulated hands and basic facial features) using the extracted pose data, visualizing signs in a clear, accessible way.
- **Modular Pipeline:** Designed for easy extension to 3D avatars, real-time translation, or integration with browser extensions.

---

## Project Motivation

Millions of people rely on sign language as their primary means of communication, yet most online content is inaccessible to them. Our project leverages AI to translate video/audio/text into sign language animations, making educational and informational content barrier-free.

---

## Pipeline Overview

1. **Data Preparation**
    - Source: [ASLLVD Dataset](https://www.bu.edu/asllrp/), with sign video metadata in Excel format.
    - Video segmentation: Extracts individual sign clips from full videos using frame indices.

2. **Pose Estimation**
    - Utilizes [MMPose](https://github.com/open-mmlab/mmpose) and [RTMPose](https://github.com/open-mmlab/mmpose/tree/main/projects/rtmpose) for 2D keypoint extraction.
    - Outputs `.npz` files containing (x, y, confidence) for 133 keypoints per frame.

3. **Sign Gloss Mapping**
    - Each sign gloss is mapped to its corresponding pose data, building a JSON-based "sign dictionary."

4. **2D Avatar Animation**
    - Animates a 2D character using Pygame, visualizing the full body, articulated hands, and basic facial features.
    - Generates MP4 videos for each sign, suitable for web or educational use.

---

## Example Results

- ![Example Animation](./example_animation.gif)  
  *Above: 2D avatar performing the sign for "MOST" with articulated hands.*

---

## How to Run

1. **Environment:**  
   - Python 3.8+  
   - [Kaggle Notebook](https://www.kaggle.com/) or local Jupyter environment  
   - Dependencies: `mmpose`, `mmdetection`, `mmcv`, `pygame`, `Pillow`, `opencv-python`, `ffmpeg`

2. **Steps:**
   1. Upload the ASLLVD Excel metadata and source videos.
   2. Run the notebook cells in order:
      - Data loading and segmentation
      - Pose extraction
      - Sign-to-pose mapping
      - 2D avatar animation (Pygame)
   3. Download the generated MP4 animations from the output directory.

3. **Customization:**
   - To add new signs, update the Excel metadata and rerun the pipeline.
   - To improve avatar quality, replace placeholder sprites with custom artwork or extend to 3D.

---

## Project Structure
