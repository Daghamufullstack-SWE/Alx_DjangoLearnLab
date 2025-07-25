
ADVANCE FEATURES AND SECURITY

ONE:
0. Implementing a Custom User Model in Django
mandatory
Objective: Customize Django’s user model to suit the specific needs of your application, demonstrating an understanding of extending Django’s authentication system.

Task Description:
For this task, you will replace Django’s default user model with a custom user model that includes additional fields and functionality. This is a critical feature for applications that require user attributes beyond Django’s built-in user model.

Step 1: Set Up the Custom User Model
Duplicate the previous Django project directory django-models and rename it to advanced_features_and_security
Create a custom user model by extending AbstractUser, adding custom fields that are relevant to your application’s needs.

Fields to Add:

date_of_birth: A date field.
profile_photo: An image field.
Step 2: Update Settings to Use the Custom User Model
Configure Django to use this custom user model for all user-related functionalities.

Settings Configuration:
In your project’s settings.py, set the AUTH_USER_MODEL to point to your new custom user model.
Step 3: Create User Manager for Custom User Model
Implement a custom user manager that handles user creation and queries, ensuring it can manage the added fields effectively.

Custom Manager Functions to Implement:
create_user: Ensure it handles the new fields correctly.
create_superuser: Ensure administrative users can still be created with the required fields.
Step 4: Integrate the Custom User Model into Admin
Modify the Django admin to support the custom user model, ensuring that administrators can manage users effectively through the Django admin interface.

Admin Modifications Required:
Define a custom ModelAdmin class that includes configurations for the additional fields in your user model.
Step 5: Update Your Application to Use the Custom User Model
Adjust any part of your application that references the user model to use the new custom model.

Application Updates:
Update all foreign keys or user model references in your other models to use the custom user model.
Deliverables:
models.py: Include your custom user model and custom user manager.
admin.py: Set up the admin interface to manage the custom user model effectively.
settings.py: Modify to specify the custom user model as the default for the project.

TWO:
1. Managing Permissions and Groups in Django
mandatory
Objective: Implement and manage permissions and groups to control access to various parts of your Django application, enhancing security and functionality.

Task Description:
Develop a system within your Django application that utilizes groups and permissions to restrict access to certain parts of your application. This task will demonstrate your ability to set up detailed access controls based on user roles and their assigned permissions.

Step 1: Define Custom Permissions in Models
Add custom permissions to one of your existing models (or a new model if preferable) to control actions such as viewing, creating, editing, or deleting instances of that model.

Model Permissions to Add:
Create permissions such as can_view, can_create, can_edit, and can_delete within your chosen model.
Step 2: Create and Configure Groups with Assigned Permissions
Set up user groups in Django and assign the newly created permissions to these groups. Use Django’s admin site to manage these groups and their permissions.

Groups to Setup:
Create groups like Editors, Viewers, and Admins.
Assign appropriate permissions to each group. For example, Editors might have can_edit and can_create permissions.
Step 3: Enforce Permissions in Views
Modify your views to check for these permissions before allowing users to perform certain actions. Use decorators such as permission_required to enforce these permissions in your views.

Views to Modify or Create:
Ensure views that create, edit, or delete model instances check for the correct permissions.
Example: Use @permission_required('app_name.can_edit', raise_exception=True) to protect an edit view.
Step 4: Test Permissions
Manually test the implementation by assigning different users to groups and verifying that the permissions are enforced correctly.

Testing Approach:
Create test users and assign them to different groups.
Log in as these users and attempt to access various parts of the application to ensure that permissions are applied correctly.
Step 5: Document the Setup
Provide a concise guide or notes within your code on how the permissions and groups are set up and used in the application.
This could be in the form of comments or a simple README file.
make sure to use the variable name as defined above such as can_edit, can_create.
Deliverables:
models.py: Updated with custom permissions for at least one model.
views.py: Updated to include permission checks in relevant views.
Documentation: Comments or a README file explaining how permissions and groups are configured and used.
Repo:

GitHub repository: Alx_DjangoLearnLab
Directory: advanced_features_and_security
 
2. Implementing Security Best Practices in Django
mandatory
Objective: Apply best practices for securing a Django application. This task will guide you through enhancing the security of your application by configuring various Django settings and writing secure code.

Task Description:
Implement several security measures in your Django project to protect against common vulnerabilities such as cross-site scripting (XSS), cross-site request forgery (CSRF), and SQL injection. This will involve configuring settings and modifying templates and views to enforce these protections.

Step 1: Configure Secure Settings
Adjust Django settings to enhance the security of your application. Focus on settings that prevent security vulnerabilities and ensure data privacy.

Security Settings to Configure:
Set DEBUG to False in production.
Configure SECURE_BROWSER_XSS_FILTER, X_FRAME_OPTIONS, and SECURE_CONTENT_TYPE_NOSNIFF to add additional browser-side protections.
Ensure CSRF_COOKIE_SECURE and SESSION_COOKIE_SECURE are set to True to enforce that cookies are sent over HTTPS only.
Step 2: Protect Views with CSRF Tokens
Ensure that all your forms use CSRF tokens to protect against CSRF attacks. This involves modifying form templates to include {% csrf_token %}.

Template Modifications:
Update form templates to explicitly include the CSRF token tag if not already present.
Step 3: Secure Data Access in Views
Modify views to avoid SQL injection and ensure safe handling of user input, especially in search functionalities or where direct SQL queries are used.

Views to Secure:
Use Django’s ORM properly to parameterize queries instead of string formatting.
Validate and sanitize all user inputs using Django forms or other validation methods.
Step 4: Implement Content Security Policy (CSP)
Set up a Content Security Policy header to reduce the risk of XSS attacks by specifying which domains can be used to load content in your application.

Setting up CSP:
Use Django’s django-csp middleware or manually set the CSP header in your response objects.
Step 5: Documentation and Testing
Document the security measures implemented, and conduct basic security tests to ensure configurations are effective.

Documentation:
Comment within your code on how and why specific security settings or practices are implemented.
Testing Approach:
Manually test the application to check for secure handling of inputs and responses. Test forms and input fields for CSRF and XSS vulnerabilities.
Deliverables:
settings.py: Updated with secure configurations.
Templates: Updated to include CSRF tokens and other necessary security enhancements.
views.py: Securely coded to prevent SQL injections and handle user inputs safely.
Documentation: Comments or a separate document detailing the security measures implemented.
Project structure
LibraryProject/
│
├── LibraryProject/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│
├── bookshelf/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py
│   ├── migrations/
│   │   ├── __init__.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   ├── views.py
│   └── templates/
│       └── bookshelf/
│           ├── book_list.html
│           ├── form_example.html
│
├── manage.py

:

THREE:
3. Implementing HTTPS and Secure Redirects in Django
mandatory
Objective: Enhance the security of your Django application by configuring it to handle secure HTTPS connections and enforce HTTPS redirects for all HTTP requests. This task will ensure that your application adheres to best practices for secure web communication.

Task Description:
Configure your Django application to support and enforce HTTPS, protecting the data transmitted between the client and the server. This includes setting up HTTPS redirects, configuring security-related headers, and ensuring that your site is served securely.

Step 1: Configure Django for HTTPS Support
Adjust your Django settings to strengthen the security of your application by enforcing HTTPS connections.

Security Settings to Adjust:
SECURE_SSL_REDIRECT: Set to True to redirect all non-HTTPS requests to HTTPS.
SECURE_HSTS_SECONDS: Set an appropriate value (e.g., 31536000 for one year) to instruct browsers to only access the site via HTTPS for the specified time.
SECURE_HSTS_INCLUDE_SUBDOMAINS and SECURE_HSTS_PRELOAD: Set to True to include all subdomains in the HSTS policy and to allow preloading.
Step 2: Enforce Secure Cookies
Modify cookie settings to enhance security by ensuring that cookies are only sent over secure HTTPS connections.

Cookie Settings to Configure:
SESSION_COOKIE_SECURE: Set to True to ensure session cookies are only transmitted over HTTPS.
CSRF_COOKIE_SECURE: Set to True to ensure CSRF cookies are only transmitted over HTTPS.
Step 3: Implement Secure Headers
Add additional HTTP headers to further secure your application from various types of attacks like clickjacking and XSS.

Headers to Implement:
X_FRAME_OPTIONS: Set to “DENY” to prevent your site from being framed and protect against clickjacking.
SECURE_CONTENT_TYPE_NOSNIFF: Set to True to prevent browsers from MIME-sniffing a response away from the declared content-type.
SECURE_BROWSER_XSS_FILTER: Set to True to enable the browser’s XSS filtering and help prevent cross-site scripting attacks.
Step 4: Update Deployment Configuration
Ensure that your deployment environment is configured to support HTTPS by setting up SSL/TLS certificates. This might involve updating your web server configuration (e.g., Apache or Nginx) to include SSL directives and certificate files.

Step 5: Documentation and Review
Document the changes made to secure the application, particularly how HTTPS and related security settings are implemented and enforced. Review all settings to ensure they are correctly configured for your production environment.

Deliverables:
settings.py: Documented changes with detailed comments on each security setting configured.
Deployment Configuration: Instructions or scripts used to configure your web server for HTTPS, included as part of your deployment documentation.
Security Review: A brief report detailing the security measures implemented, how they contribute to securing the application, and any potential areas for improvement.
