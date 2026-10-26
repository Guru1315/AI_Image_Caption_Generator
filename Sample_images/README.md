# Sample images

Six photos for trying out the upload step of the [AI Image Caption Generator](../README.md). The caption in the table is what the BLIP model produced for each one in the saved run (`../image_caption_results.csv`).

| File | Caption generated |
|---|---|
| `sample_china_temple.jpg` | The pagoda tower at the top of the hill. |
| `sample_flower.jpg` | Two orange flowers with green leaves in the background. |
| `sample_rocket.jpg` | A spacex rocket is seen on the launch pad. |
| `sample_coffee.jpg` | A cup of coffee on a wooden table. |
| `sample_astronaut.jpg` | A astronaut with his space suit. |
| `sample_cat.jpg` | A close up of a cat with green eyes. |

Captions can differ slightly with other library versions or hardware, so yours may not match word for word.

## How to use them

1. Download the images you want to test with.
2. Open the notebook in Google Colab and run the cells in order up to the upload cell.
3. Click **Choose files** and select the images.
4. Run the remaining cells to see each image with its caption.

If you skip the upload, the notebook uses three different pictures downloaded from the COCO dataset instead, so these six are only used when you upload them.

## Adding your own

Any image the Pillow library can open will work, and files that are not valid images are skipped with a warning. Only upload pictures you have the right to use, and avoid photos of people who have not agreed to it.
