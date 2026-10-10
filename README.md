
# 🖼️ AI Image Caption Generator

An AI system that analyzes an uploaded image, identifies its main objects and activities, and generates a **human-readable caption**. Built in Google Colab using pre-trained vision-language and computer vision models, as part of an AI internship project.

## 📌 Overview

Image captioning combines **computer vision** (understanding what is in a picture) and **natural language generation** (describing it in a sentence). This project lets a user upload one or more images and returns each image with a generated caption and the objects found in it.

## ✨ Features

- Upload **one or many images** (JPG, JPEG, PNG)
- **Caption generation** using the pre-trained **BLIP** vision-language model
- **Object detection** with bounding boxes using pre-trained **DETR**
- Displays the **image together with its caption** and labelled objects
- **Alternative captions** (top 3) and **prompt-guided captions**
- Caption any image directly from a **URL**
- **CSV export** of all results
- Automatic **sample images** for a quick demo
- No training required, only pre-trained models

## 🧠 How It Works

```
Uploaded Image ─┬─► BLIP (vision-language model) ─► Caption
                └─► DETR (object detector)       ─► Objects + bounding boxes
                                    │
                                    ▼
              Image + Caption + Detected Objects displayed ─► CSV export
```

| Model | Task | Source |
|---|---|---|
| `Salesforce/blip-image-captioning-base` | Image → natural-language caption | Hugging Face |
| `facebook/detr-resnet-50` | Object detection (labels, boxes, confidence) | Hugging Face |

Captions are generated with **beam search** (5 beams) and a repetition penalty for fluent, non-repetitive sentences.

## 🛠️ Tech Stack

- **Language:** Python
- **Deep learning:** PyTorch, Hugging Face Transformers
- **Image handling:** Pillow
- **Data & visualization:** pandas, NumPy, Matplotlib
- **Platform:** Google Colab

## 🚀 Getting Started

1. Open `AI_Image_Caption_Generator.ipynb` in [Google Colab](https://colab.research.google.com).
2. Run the cells **one at a time, in order** (no installation needed).
3. When the upload cell appears, click **Choose files** and select your images. Skip it to use sample images.
4. View each image with its caption and detected objects.
5. Download `image_caption_results.csv` from the last cells.

> Tip: for faster results, enable a GPU with **Runtime → Change runtime type → T4 GPU**.

## 📂 Repository Structure

```
├── AI_Image_Caption_Generator.ipynb   # Main Colab notebook
├── sample_images/                     # Images used for testing
├── image_caption_results.csv          # Example output
└── README.md
```

## 📊 Sample Output

Add your screenshots after running the notebook:

```
![Caption result 1](images/result1.png)
![Caption result 2](images/result2.png)
```

Example format:

| Image | Caption | Objects Detected |
|---|---|---|
| your_image.jpg | *(generated caption)* | *(detected objects)* |

## ⚠️ Limitations

- Captions can be generic and may miss fine details or unusual scenes.
- Object detection only recognizes the 80 COCO categories.
- Models are English-only and not fine-tuned for any specific domain.
- Captions may reflect biases present in the training data.

## 🔮 Future Improvements

- Use larger models such as BLIP-2 or other vision-language models
- Multilingual captions and text-to-speech for accessibility
- Web interface using Gradio or Streamlit
- Fine-tuning on a custom dataset
- Evaluation with caption metrics such as BLEU and CIDEr

## 🎓 Learning Outcomes

- How AI interprets images and produces text descriptions
- Using pre-trained vision-language and object detection models
- Combining computer vision with natural language generation
- Building a simple end-to-end AI application in Colab

## 📄 License

This project was created for educational purposes as part of an AI internship.
