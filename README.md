# Passport OCR Recognition 

This repository provides a Python-based OCR (Optical Character Recognition) API for recognizing and extracting information from passports. The API supports multiple passport formats and efficiently reads various fields like passport number, name, nationality, and expiration date.

## Feacture

- Extracts key passport information (e.g., passport number, name, date of birth, nationality).
- Supports multiple passport formats and nationalities, including **Machine Readable Zones (MRZ)**.
- Fast and accurate OCR using advanced image processing techniques.
- Easy-to-use RESTful API with **JSON** response format.
- Can be deployed in a local environment or cloud-based infrastructure.
- Extendable to recognize other forms of ID documents (e.g., national IDs, visas).

## Technologies Used

- **Python**: Backend language.
- **Tesseract OCR**: For optical character recognition.
- **Flask/Django/FastAPI** (Choose one, if applicable): To expose the OCR functionality as an API.
- **OpenCV**: For pre-processing passport images.
- **Pillow**: For image manipulation.
- **Docker**: For containerization and easy deployment.

## How to use 

```import requests
import hashlib
import time

def generate_token(key, timestamp, secret):
    hash_string = f"{key}+{timestamp}+{secret}"
    return hashlib.md5(hash_string.encode()).hexdigest()

def make_request():
    key = "M***********g"
    secret = "3***********6"
    timestamp = int(time.time() * 1000)
    token = generate_token(key, timestamp, secret)

    files = {
        'key': (None, key),
        'typeId': (None, '13'),
        'timestamp': (None, str(timestamp)),
        'token': (None, token),
        'img': (None, "/9j")
    }

    response = requests.post('https://flyocr.com/api/recogliu.do', files=files)
    return response.text

if __name__ == '__main__':
    response_text = make_request()
    print(response_text)
    ```
    