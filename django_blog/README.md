## ALX CREATE FULL WEB APP WEEK 14 BE
## Initalization and configuration of the blog app
The application has a POST model that contains four main attributes which are: title, content, published_date and author (has a foreign key to Django's user model). 

## Project structure:
django_blog/
    blog/
        migrations/
        models.py
        static/
            css/
                styles.css
            js/
                scripts.js
        templates/
            blog/
                base.html
                
        views.py
    django_blog/
        settings.py
        urls.py
    manage.py
