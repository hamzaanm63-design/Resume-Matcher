ResumeMatcher

ResumeMatcher is a Flask-based web application that compares resumes with a given job description and identifies the resumes that are most relevant to the job.

It uses TF-IDF (Term Frequency–Inverse Document Frequency) to convert the job description and resumes into numerical vectors and cosine similarity to calculate how closely each resume matches the job description.

Features

Upload multiple resumes at once.

Supports:

PDF

DOCX

TXT

Enter a job description directly in the web interface.

Extracts text automatically from uploaded resumes.

Calculates resume-to-job-description similarity using TF-IDF.

Uses cosine similarity to rank resumes.

Displays the top 5 matching resumes with similarity scores.

Simple and responsive interface using Bootstrap.

Technologies Used

Python

Flask – Web application framework

Scikit-learn – TF-IDF and cosine similarity

PyPDF2 – PDF text extraction

docx2txt – DOCX text extraction

Bootstrap 5 – Frontend styling

HTML/CSS – User interface

Project Structure
ResumeMatcher/
│
├── app.py
├── templates/
│   └── matchresume.html
│
├── static/
│   └── images.png
│
├── uploads/
│
├── requirements.txt
└── README.md

Installation
1. Clone the Repository
git clone https://github.com/your-username/ResumeMatcher.git
cd ResumeMatcher

2. Create a Virtual Environment

Windows:

python -m venv venv
venv\Scripts\activate


Linux/macOS:

python3 -m venv venv
source venv/bin/activate

3. Install Dependencies

Install the required Python packages:

pip install flask docx2txt PyPDF2 scikit-learn


You can also create a requirements.txt file:

Flask
docx2txt
PyPDF2
scikit-learn


Then install them with:

pip install -r requirements.txt

Running the Application

Start the Flask application:

python app.py


The application will run locally at:

http://127.0.0.1:5000/


Open the address in your browser.

How It Works

The application follows these steps:

The user enters a job description.

The user uploads multiple resumes.

ResumeMatcher extracts text from each resume.

The job description and extracted resume text are passed to TfidfVectorizer.

TF-IDF converts the text into numerical vectors.

Cosine similarity calculates the similarity between the job description and each resume.

Resumes are sorted according to their similarity scores.

The top 5 matching resumes are displayed.

Matching Process

The core matching process uses:

vectorizer = TfidfVectorizer().fit_transform(
    [job_description] + resumes
)

similarities = cosine_similarity(
    [job_vector],
    resume_vectors
)[0]


A higher cosine similarity score indicates that the resume has more textual similarity to the job description.

Supported File Types
File Type	Supported
PDF	✅
DOCX	✅
TXT	✅
Example

Suppose the job description contains:

Python developer with experience in Flask,
machine learning, SQL, and REST APIs.


The application compares this description against all uploaded resumes.

The results may look like:

Top matching resumes:

resume_2.pdf (Similarity Score: 0.78)
resume_5.docx (Similarity Score: 0.71)
resume_1.pdf (Similarity Score: 0.65)
resume_4.txt (Similarity Score: 0.59)
resume_3.pdf (Similarity Score: 0.52)


The scores are based on textual similarity and should not be interpreted as a complete assessment of a candidate's qualifications.

Important Notes

Upload more than 5 resumes for meaningful comparison.

The current implementation returns the top 5 resumes.

Scanned/image-only PDFs may not produce useful text because PyPDF2 relies on text extraction rather than OCR.

The matching system is based on textual similarity and does not understand qualifications in the same way a human recruiter would.

Uploaded files are currently stored in the uploads/ directory.

Future Improvements

Possible improvements include:

Add OCR support for scanned resumes.

Extract and compare specific skills.

Add experience and education matching.

Improve text preprocessing.

Add keyword/skill-based matching.

Add a candidate ranking dashboard.

Allow users to download matching results.

Add authentication and user accounts.

Delete uploaded files after processing.

Add file-size and file-type validation.

Deploy the application to a cloud platform.

Improve security around uploaded files.

License

This project is intended for educational and personal use. You can modify and extend it according to your requirements.

Author

Your Name

If you found this project useful, consider giving the repository a ⭐ on GitHub.
