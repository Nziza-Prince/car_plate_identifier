# Car Number Plate Recognition System

My Y3 project for automatic license plate detection and reading. Based on the book "Car Number Plate Extraction in Three Steps".

## What it does

Captures video from webcam and automatically reads car license plates using computer vision.

## Project Structure
```
src/
  camera.py       - tests if camera works
  detect.py       - finds plates using contours
  align.py        - fixes the angle/perspective
  ocr.py          - reads the text with Tesseract
  validate.py     - checks if format is correct
  temporal.py     - full system with CSV logging

data/
  logs/           - CSV files with detected plates
  plates/         - saved plate images
```

## How it works

1. **Detection** - Finds rectangular shapes that look like plates (checks size and aspect ratio)
2. **Alignment** - Warps the plate to 450x140 pixels so it's straight
3. **OCR** - Uses Tesseract to read the characters
4. **Validation** - Checks format: 3 letters + 3 numbers + 1 letter (like RAD123A)
5. **Temporal check** - Confirms the same plate across multiple frames to avoid errors
6. **Save** - Logs to CSV with timestamp

## Setup

Need Python 3.8+ and a webcam.

```bash
# create virtual environment
python3 -m venv venv
source venv/bin/activate

# install packages
pip install opencv-python numpy pytesseract pandas
```

### Install Tesseract
- Ubuntu: `sudo apt install tesseract-ocr`
- macOS: `brew install tesseract`

## Running the project

Test each part:
```bash
python src/camera.py      # check camera
python src/detect.py      # test detection
python src/align.py       # test alignment
python src/ocr.py         # test OCR
python src/validate.py    # test validation
python src/temporal.py    # run full system
```

Press `q` to quit.

## Testing

Tested on real cars at school parking. Works best with:
- Good lighting
- 2-5 meters distance
- Clean plates
- Camera pointing straight

## Issues I found

- Sometimes mixes up B/8 and O/0
- Doesn't work well in bad lighting or at extreme angles
- Need to be fairly close to the vehicle

## Dependencies

- opencv-python
- numpy
- pytesseract
- pandas
