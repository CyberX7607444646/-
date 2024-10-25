# -
𝗧𝗵𝗶𝘀 𝘁𝗼𝗼𝗹 𝘂𝘀𝗲 𝗶𝘀 𝗼𝗻𝗹𝘆 𝗳𝗼𝗿 𝗲𝗱𝘂𝗰𝗮𝘁𝗶𝗼𝗻𝗮𝗹 𝗽𝗼𝗿𝗽𝗮𝘀𝗲𝘀𝘀 😈
For more Blackhat tools Contect me Thanks ☠️


import requests
from bs4 import BeautifulSoup
import re
import subprocess
import sys
import os
from colorama import init, Fore
from concurrent.futures import ThreadPoolExecutor
import random
import time
import argparse
import json
import sqlite3
from stem import Signal
from stem.control import Controller
from fake_useragent import UserAgent
import socks
import socket
from elasticsearch import Elasticsearch
from selenium import webdriver
import csv
import spacy  # For NLP-based entity recognition

init(autoreset=True)

# Initialize Elasticsearch for advanced search indexing
es = Elasticsearch()

# Set up OCR for image/PDF processing
try:
    import pytesseract
    from PIL import Image
except ImportError:
    subprocess.check_call([sys.executable, "-m", "pip", "install", "pytesseract", "pillow"])

# Initialize NLP Model
nlp = spacy.load("en_core_web_sm")

# Function to install necessary libraries
def install_libraries():
    try:
        import requests
        import bs4
        import colorama
        import stem
        import fake_useragent
        import spacy
    except ImportError:
        subprocess.check_call([sys.executable, "-m", "pip", "install", 'requests', 'bs4', 'colorama', 'stem', 'fake_useragent', 'spacy'])
        spacy.cli.download("en_core_web_sm")

# Function to set up Tor for anonymity
def setup_tor_proxy():
    controller = Controller.from_port(port=9051)
    controller.authenticate(password="your_password")  # Set this up in your Tor config
    controller.signal(Signal.NEWNYM)  # Change identity
    socks.set_default_proxy(socks.SOCKS5, "127.0.0.1", 9050)  # Set Tor as proxy
    socket.socket = socks.socksocket

# Function to parse and analyze content using NLP
def analyze_text(text):
    doc = nlp(text)
    entities = [(entity.text, entity.label_) for entity in doc.ents]
    return entities

# OCR Function for PDF/Image parsing
def extract_text_from_image(file_path):
    return pytesseract.image_to_string(Image.open(file_path))

# Elasticsearch indexing function
def index_result(query, link, content):
    es.index(index="cyber_x_osint", document={"query": query, "link": link, "content": content})

# Function to fetch search results and analyze content with NLP
def fetch_and_analyze_results(url):
    try:
        response = requests.get(url, headers={"User-Agent": get_random_user_agent()})
        if response.status_code == 200:
            content = response.text
            entities = analyze_text(content)
            index_result("sample query", url, content)
            print(f"Entities found: {entities}")
    except Exception as e:
        print(f"Error analyzing content from {url}: {e}")

# Enhanced reporting function with CSV/JSON export
def save_report(links, query, format="csv"):
    if format == "csv":
        with open(f"{query}_report.csv", "w", newline='', encoding='utf-8') as f:
            writer = csv.writer(f)
            writer.writerow(["Link", "Extracted Entities"])
            for link in links:
                writer.writerow([link, fetch_and_analyze_results(link)])
    elif format == "json":
        with open(f"{query}_report.json", "w", encoding="utf-8") as f:
            json.dump(links, f)

# Enhanced Command Line Interface with more options
def setup_arg_parser():
    parser = argparse.ArgumentParser(description="Cyber-X Advanced OSINT Tool")
    parser.add_argument('--query', type=str, help="Search query for OSINT", required=True)
    parser.add_argument('--output-format', type=str, choices=["csv", "json"], default="csv", help="Report format")
    parser.add_argument('--use-tor', action='store_true', help="Enable Tor network")
    parser.add_argument('--language', type=str, default="en", help="Language for OCR and NLP")
    return parser.parse_args()

# Main function
def main():
    install_libraries()
    args = setup_arg_parser()

    if args.use_tor:
        setup_tor_proxy()
        print(f"{Fore.YELLOW}Using Tor network for anonymous searching...")

    # Placeholder for performing search and fetching results
    # Here, you would loop through dorks and collect results

    # Example dummy result for illustration
    links = ["https://example.com/data"]

    # Save analyzed results in chosen format
    save_report(links, args.query, args.output_format)

if __name__ == "__main__":
    main()



This Code is copy for this place create a new file choose you file name foe exampile ( Cyber_X.py ) paste this code on the file and save.



(1)

farst install requirements 👻
requirements command down bellowe 😈


1  sudo apt update
sudo apt install python3 python3-pip tor tesseract-ocr -y



2   pip3 install requests beautifulsoup4 colorama stem fake_useragent spacy elasticsearch selenium pytesseract pillow


3   python3 -m spacy download en_core_web_sm

4   sudo nano /etc/tor/torrc

ControlPort 9051
HashedControlPassword your_password

sudo systemctl restart tor


5  sudo apt install chromium-driver -y

sudo apt install firefox-esr -y
sudo apt install geckodriver -y

6  python3 cyber_x.py --query "example search" --output-format csv --use-tor

𝗲𝘅𝗮𝗺𝗽𝗶𝗹 𝗰𝗼𝗺𝗺𝗮𝗻𝗱 ( python3 cyber_x.py --query "sensitive information" --output-format csv )

1  ( python3 cyber_x.py --query "confidential data" --output-format json --use-tor )

2 ( python3 cyber_x.py --query "scanned documents" --output-format csv --use-tor )

