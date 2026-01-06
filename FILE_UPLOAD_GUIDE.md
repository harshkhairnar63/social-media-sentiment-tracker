# File Upload Sentiment Analysis Guide

## Overview
You can now upload files containing comments to analyze sentiment. The application supports CSV, PDF, and Word (.docx) files.

## Supported File Formats

### 1. CSV Files
CSV files should have the following columns:
- **text** or **comment** or **message** (required) - The comment text
- **author** or **user** or **name** (optional) - The author's name
- **timestamp** or **date** or **time** (optional) - When the comment was made

#### Sample CSV Format:
```csv
text,author,timestamp
"This product is amazing! I love it.",John Doe,2024-01-15
"Terrible experience. Very disappointed.",Jane Smith,2024-01-16
"It's okay, nothing special.",Bob Johnson,2024-01-17
"Great customer service and fast delivery!",Alice Brown,2024-01-18
"Not worth the price. Poor quality.",Charlie Wilson,2024-01-19
```

### 2. PDF Files
- Text is automatically extracted from the PDF
- Comments are split by paragraphs
- Each paragraph with more than 10 characters is treated as a separate comment

### 3. Word Documents (.docx)
- Text is automatically extracted from the document
- Comments are split by paragraphs
- Each paragraph with more than 10 characters is treated as a separate comment

## How to Use

1. Click the "Choose File" button on the dashboard
2. Select your CSV, PDF, or Word file
3. Wait for the file to be processed
4. View the sentiment analysis results immediately

The analyzed comments will be:
- Added to the mention list
- Included in the sentiment statistics
- Displayed in the charts

## Installation

To use this feature, you need to install additional dependencies:

```bash
npm install papaparse mammoth pdfjs-dist
npm install --save-dev @types/papaparse
```

## Sample Test Files

### Create a test CSV file (comments.csv):
```csv
text,author,timestamp
"Absolutely love this product! Best purchase ever.",Sarah Johnson,2024-01-20
"Had some issues initially but customer service resolved them quickly.",Mike Davis,2024-01-20
"Not what I expected. Quality could be better.",Emma Wilson,2024-01-21
"Amazing features and easy to use!",David Lee,2024-01-21
"Waste of money. Very disappointed.",Lisa Brown,2024-01-22
"Good value for the price. Recommended!",Tom Anderson,2024-01-22
"The worst experience I've had. Avoid at all costs.",Rachel Green,2024-01-23
"Pretty decent. Does what it says.",Chris Martin,2024-01-23
"Excellent product! Exceeded my expectations.",Jennifer White,2024-01-24
"Poor customer support. No response to my queries.",Kevin Taylor,2024-01-24
```

## Troubleshooting

### "No comments found in the file"
- For CSV: Make sure you have a column named 'text', 'comment', or 'message'
- For PDF/Word: Ensure the document contains paragraphs with at least 10 characters

### "Unsupported file type"
- Only .csv, .pdf, .doc, and .docx files are supported
- Check that your file has the correct extension

### Processing takes too long
- Large files may take a few seconds to process
- PDF files with many pages may take longer
- Consider splitting very large files into smaller chunks
