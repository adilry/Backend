import pdfplumber
import re

def extract_text_from_pdf(pdf_path):
    with pdfplumber.open(pdf_path) as pdf:
        text = ''
        for page_number in range(len(pdf.pages)):
            page = pdf.pages[page_number]
            text += page.extract_text()

    return text

def clean_text(text):
    cleaned_text = re.sub(r'\s*PRESIDEN\s+REPUBLIK\s+INDONESIA\s+-\s+\d+\s+-\s*\n', '\n', text)
    cleaned_text = '\n'.join(line.strip() for line in cleaned_text.split('\n') if line.strip())
    return cleaned_text

pdf_path = 'input.pdf'
text_from_pdf = extract_text_from_pdf(pdf_path)
cleaned_text = clean_text(text_from_pdf)

output_txt_path = 'output.txt'
with open(output_txt_path, 'w', encoding='utf-8') as txt_file:
    txt_file.write(cleaned_text)

print(f'Text has been saved to {output_txt_path}')
