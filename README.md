# Excel-Web-App

Deploying your Streamlit dashboard with Heroku

Streamlit is an open-source Python framework that allows you to create beautiful interactive websites for Machine Learning and Data Science projects without needing to have any web development skills.

Building an example application
To show how to deploy a Streamlit application we first need to create one.

Heroku deployment
Now that we have our application we are ready to start deploying the application to Heroku.

1. Needed files
First, you need to add some files that allow Heroku to install the needed requirements and run the application.

requirements.txt
The requirements.txt file contains all the libraries that need to be installed for the project to work. This file can be created manually by going through all files and looking what libraries are used or automatically using something like pipreqs.

pipreqs <directory-path>

The requirements file should look something like the following:

streamlit==0.79.0
pandas==1.2.3
numpy==1.18.5
matplotlib==3.3.2
seaborn==0.11.0
scikit_learn==0.24.1
  
setup.sh and Procfile
  
Using the setup.sh and Procfile files you can tell Heroku the needed commands for starting the application.

In the setup.sh file we will create a streamlit folder with a credentials.toml and a config.toml file.

mkdir -p ~/.streamlit/

echo "\
[general]\n\
email = \"your-email@domain.com\"\n\
" > ~/.streamlit/credentials.toml

echo "\
[server]\n\
headless = true\n\
enableCORS=false\n\
port = $PORT\n\
" > ~/.streamlit/config.toml
  
The Procfile is used to first execute the setup.sh and then call streamlit run to run the application.

web: sh setup.sh && streamlit run app.py

2. Creating a Git repository

3. Create a Heroku Account

4. Installing the Heroku Command Line Interface (CLI)

5. Login to Heroku

heroku login

6. Deploy the Application

git add .
git commit -m "some message"
git push heroku master

7. Check if it is running

  You can check if the application was deployed successfully using heroku ps:scale web=1.
