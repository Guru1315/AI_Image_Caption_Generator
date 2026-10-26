
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
├── Sample_images/                     # Six photos used for testing
│   └── README.md                      # What each photo is
├── image_caption_results.csv          # Example output for those six photos
└── README.md
```

### Two kinds of sample images

- **Built-in demo images.** If you skip the upload cell, the notebook downloads three pictures from the COCO dataset (two cats, a room and a bedroom). This needs internet access from Colab.
- **`Sample_images/` folder.** Six photos you can download and upload yourself. `image_caption_results.csv` was made by running these six.

## ⚙️ Settings in the notebook

| Setting | Default | Where |
|---|---|---|
| Beam search | 5 beams (at least as many as the captions you ask for) | `generate_caption` |
| Repetition penalty | 1.3 | `generate_caption` |
| Maximum caption length | 40 new tokens | `generate_caption` |
| Object confidence threshold | 0.85 (detections below 85% are dropped) | `detect_objects` |
| Prompt-guided examples | "a photography of", "a picture showing", "this is an image of" | the alternative-captions cell |

DETR is loaded with `revision="no_timm"`, which avoids needing the `timm` package. If the detector fails to load, the notebook prints a warning and carries on with captions only.

## 📊 Sample Output

`image_caption_results.csv` holds the results for the six images in `Sample_images/`:

| Image | Caption |
|---|---|
| sample_china_temple.jpg | The pagoda tower at the top of the hill. |
| sample_flower.jpg | Two orange flowers with green leaves in the background. |
| sample_rocket.jpg | A spacex rocket is seen on the launch pad. |
| sample_coffee.jpg | A cup of coffee on a wooden table. |
| sample_astronaut.jpg | A astronaut with his space suit. |
| sample_cat.jpg | A close up of a cat with green eyes. |

The CSV columns are **No, Image, Caption, Objects Detected, Object Count**.

> **Note on the saved results:** in this file every image shows `none detected` and a count of 0, even the cat photo. A cat is one of the 80 COCO categories DETR knows, so this most likely means the detector did not load in that run and the notebook continued with captions only. If you run the notebook yourself, check the model-loading cell for the line `✅ DETR object detector loaded`. If it shows the warning instead, the Objects column will be empty.

The notebook also draws each image with green bounding boxes and labels for the objects it finds. Screenshots are not in the repository yet.

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
