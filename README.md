# Campus-Recruitment-Management-System
This Project is about Campus recruitment System where both IT companies as well as student can register themselves on the on the same platform to interact with each other.
 ## Technologies Used:
 - Python 3.13
 - Django 5.2
 - HTML5
 - CSS3 
 - Javascipt
 > This is how the home page looks
 ![Screenshot from 2019-12-06 14-22-15](https://user-images.githubusercontent.com/42781233/70318900-1d355300-1847-11ea-9594-023c571992e2.png)
 

 ![Screenshot (61)](https://user-images.githubusercontent.com/42781233/91100568-12e01100-e683-11ea-91a8-6c2728e1b915.png)

 > Do clone the repo to see the actual website
 Follow the steps:
 - `git clone  https://github.com/ksrrock/Campus_placement_management_system.git`
 - cd into the clone folder.
 - If you are an ubuntu user activate the virtualenv as this
   `source venv/bin/activate`
 - `cd crs`
 - `python3 manage.py runserver`
 
 Copy and Paste the URL to visit the Website

## Run locally with current Python

```powershell
cd Campus-Recruitment-Management-System-master
py -3.13 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python crs\manage.py migrate
python crs\manage.py runserver
```

Open http://127.0.0.1:8000/

## Deploy to Render

The project is configured for Render with Gunicorn, WhiteNoise, and PostgreSQL support.

1. Create a GitHub repository and upload this folder. From PowerShell:

   ```powershell
   cd C:\Users\18110\Desktop\Campus-Recruitment-Management-System
   git init
   git add .
   git commit -m "Prepare campus recruitment app for deployment"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
   git push -u origin main
   ```

   Do not add `.venv`, `.env`, or `crs\db.sqlite3`; these are excluded by `.gitignore`.

2. In Render, create a PostgreSQL database and a **Web Service** connected to the GitHub repository.
3. Use these Web Service commands:

   **Build command**

   ```text
   pip install -r requirements.txt && python crs/manage.py migrate && python crs/manage.py collectstatic --noinput
   ```

   **Start command**

   ```text
   gunicorn --chdir crs crs.wsgi:application --bind 0.0.0.0:$PORT
   ```

4. Add these environment variables to the web service:

   - `DATABASE_URL`: the PostgreSQL database's internal connection URL from Render
   - `DJANGO_SECRET_KEY`: generate a unique key locally with `python -c "import secrets; print(secrets.token_urlsafe(50))"`
   - `DJANGO_DEBUG`: `False`
   - `DJANGO_ALLOWED_HOSTS`: your Render hostname, e.g. `your-app.onrender.com` (no `https://`)
   - `CSRF_TRUSTED_ORIGINS`: `https://your-app.onrender.com`

5. Deploy. Open the Render URL when the build completes. If you change code later, push the changes to GitHub and Render will redeploy.
 
