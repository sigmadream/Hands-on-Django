# hands-on-django

## mysite
    
> [장고 5.0 튜토리얼 Hands-On](https://docs.djangoproject.com/en/5.0/)을 진행

### 파이썬 설치 및 VSCode 개발 환경 구성
- Python 3.12
- VSCode 최신버전
    - 플러그인 설치 : Python(Microsoft에서 제공하는 것)
- VSCode - Terminal - New Terminal
    - pip list
    - pip install django
    - pip list > "Django   5.0"을 확인하세요!

### 주의사항
- Django 연습하실 때, 어떤 파이썬을 사용하시는지 꼭 확인하세요.
	- Anaconda
	- Minconda
	- Python v3.11
	- Python v3.12

## Django 튜토리얼

### Part 1: Requests and responses

```bash
$ python -m django --version
5.0

$ django-admin startproject mysite .

$ python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
December 08, 2023 - 01:10:44
Django version 5.0, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```

### Part 2: Models and the admin site

```bash
$ python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK

# setting.py에 등록(INSTALLA_APPS) 후에

$ python manage.py makemigrations polls
Migrations for 'polls':
  polls\migrations\0001_initial.py
    - Create model Question
    - Create model Choice

$ python manage.py sqlmigrate polls 0001

BEGIN;
--
-- Create model Question
--
CREATE TABLE "polls_question" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "question_text" varchar(200) NOT NULL, "pub_date" datetime NOT NULL);
--
-- Create model Choice
--
CREATE TABLE "polls_choice" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "choice_text" varchar(200) NOT NULL, "votes" integer NOT NULL, "question_id" bigint NOT NULL REFERENCES "polls_question" ("id") DEFERRABLE INITIALLY DEFERRED);
CREATE INDEX "polls_choice_question_id_c5b4b260" ON "polls_choice" ("question_id");
COMMIT;

$ python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, polls, sessions
Running migrations:
  Rendering model states... DONE
  Applying polls.0001_initial... OK

# python maage.py shell을 이용해서 데이터베이스 객체를 다루는 방법을 간단하게 알아봄

$ python manage.py createsuperuser
Username (leave blank to use 'sigma'): admin
Email address: admin@test.com
Password: 
Password (again): 
This password is too common.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.
➜ mysite git:(main) python manage.py runserver      
Watching for file changes with StatReloader
Performing system checks...

# 데이터베이스 객체를 admin에 등록 후에 활용
```

### Part 3: Views and templates
### Part 4: Forms and generic views
### Part 5: Testing
### Part 6: Static files
### Part 7: Customizing the admin site
### Part 8: Adding third-party packages