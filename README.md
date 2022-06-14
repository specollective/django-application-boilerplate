# Insights Agent API

🚧 This repository is actively under development and should be consider unstable. 🚧

This service exposes a RESTful JSON API and administration panel for the Insights Agent application.

# Contributing

Clone repository the git repository.
```Shell
git clone git@github.com:specollective/insights-agent-api.git
cd insights-agent-api
```

## Software Architecture

```
├── README.md
├── api
│   ├── __init__.py
│   ├── __pycache__
│   ├── admin.py
│   ├── apps.py
│   ├── auth.py
│   ├── migrations
│   ├── models.py
│   ├── serializers.py
│   ├── services.py
│   ├── tests
│   ├── utils.py
│   └── views.py
├── bin
│   ├── docs
│   ├── install
│   ├── lint
│   ├── serve
│   └── test
├── config
│   ├── __init__.py
│   ├── __pycache__
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── pages
│   ├── __init__.py
│   ├── __pycache__
│   ├── admin.py
│   ├── apps.py
│   ├── migrations
│   ├── models.py
│   ├── templates
│   ├── tests.py
│   ├── urls.py
│   └── views.py
└── requirements.txt
```

# Development Environment (localhost)

1. Set up environment variables
```Shell
cp .env.development .env
```

2. Set up python environment
```Shell
python3 -m venv python-env
```

3. Active python environment
```Shell
source python-env/bin/activate
```

4. Install dependencies
```Shell
pip install -r requirements.txt
```

5. Migrate database
```Shell
python manage.py migrate
```

7. Creating an admin user
```Shell
python manage.py createsuperuser --email example@example.com --username admin
```

8. Running development server
```Shell
python manage.py runserver
```

9. Running tests
```Shell
python manage.py test
```

10. Setting breakpoints for debugging
```Python
# Import ipdb at top of file
import ipdb
# Set interactive debugger in the code your
ipdb.set_trace()
```

11. Test basic SMS API
```
curl -X POST https://insights-agent-api.specollective.org/api/resend_access_code \
     -d '{"phone_number": "+18888888888", "name": "John Shmo"}' \
     -H 'Content-Type: application/json'
```

**Note:** Right now, we are using a trial Twilio phone number for testing. Your phone number needs to be added to the verified caller list to be able to test sending messages to your phone number.

12. Local SSL setup

https://timonweb.com/django/https-django-development-server-ssl-certificate/

# Cors resources

Set-cookies for cross-origin requests
https://stackoverflow.com/questions/46288437/set-cookies-for-cross-origin-requests

Changing local domain
https://stackoverflow.com/questions/58715204/how-to-change-the-domain-name-on-a-local-deployed-react-app

A practical, Complete Tutorial on HTTP cookies
https://www.valentinog.com/blog/cookies


curl -X POST http://localhost:8000/api/send_access_code \
  -d '{"phone_number": "+18888888888"}' \
  -H 'Content-Type: application/json'

curl -X POST http://localhost:8000/api/confirm_access_code \
  -d '{"access_code": "366997"}' \
  -H 'Content-Type: application/json'
