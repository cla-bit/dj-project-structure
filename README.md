# Django Project Structure

---

The structure follows domain-driven design principles, emphasizes modular development, and incorporates best practices for both traditional Django and Django REST Framework (DRF) projects.


## Project Root Structure

```bash

my-project/
├── applications/          # Collection of features/applications
├── configurations/        # Project configurations
├── core/                  # System-wide/global attributes
├── logging_config/        # Logging configurations
├── static/                # Static files (JS, CSS, images)
├── templates/             # HTML templates
├── tests/                 # Test functionalities
├── utilities/             # Shared/global utilities
├── manage.py              # Django's command-line utility
├── pyproject.toml         # Project metadata and dependencies
├── README.md              # Project documentation
└── .env                   # Environment variables
```


## Detailed Directory Structure

### 1. Applications Directory ( `applications/` )

The applications directory houses all feature-specific Django apps. Each application represents a distinct business capability or domain.

```bash

applications/
├── __init__.py
└── feature/               # Individual feature/app
    ├── apis/              # API/Presentation layer
    │   ├── serializers/   # Feature-specific serializers
    │   │   └── __init__.py
    │   ├── validators/    # Feature-specific validators
    │   │   └── __init__.py
    │   ├── views/         # HTTP request/response handlers
    │   │   └── __init__.py
    │   ├── __init__.py
    │   ├── filters.py     # Feature-specific filters
    │   ├── permissions.py # Feature-specific permissions
    │   └── urls.py        # Feature URL endpoints
    ├── clients/           # External service communication (optional)
    │   └── __init__.py
    ├── event_handlers/    # Feature-specific signals
    │   └── __init__.py
    ├── exceptions/        # Feature-specific exception handling
    │   └── __init__.py
    ├── selectors/         # Complex database query logic
    │   └── __init__.py
    ├── jobs/              # Scheduled jobs/tasks
    │   ├── __init__.py
    │   └── tasks.py       # Feature-specific tasks
    ├── management/        # Custom management commands
    │   ├── commands/
    │   │   ├── __init__.py
    │   │   └── my_command.py
    │   └── __init__.py
    ├── migrations/        # Database migrations
    │   └── __init__.py
    ├── models/            # Model classes
    │   └── __init__.py
    ├── services/          # Business rules and orchestration
    │   ├── __init__.py
    │   └── dto.py         # Data Transfer Objects
    ├── __init__.py
    ├── admin.py           # Django admin configuration
    ├── apps.py            # App configuration
    └── constants.py       # Feature-specific constants
```

### 2. Configurations Directory ( `configurations/` )

Contains all project-level configuration files and settings.

```bash

configurations/
├── library_configs/       # Third-party configurations
│   ├── __init__.py
│   ├── aws.py             # AWS configuration
│   └── celery.py          # Celery configuration
├── settings/              # Environment-specific settings
│   ├── __init__.py
│   ├── base.py            # Base settings
│   ├── development.py     # Development settings
│   ├── production.py      # Production settings
│   └── staging.py         # Staging settings
├── __init__.py
├── asgi.py                # ASGI configuration
├── env.py                 # Environment variable handling
├── urls.py                # Root URL configuration
└── wsgi.py                # WSGI configuration
```

### 3. Core Directory ( `core/` )

Contains system-wide components and global attributes.

```bash

core/
├── __init__.py
├── authentication.py      # Global authentication classes
├── constants.py           # System-wide constants
├── context_processors.py  # System-wide context processors
├── exceptions.py          # Global exception handlers
├── middleware.py          # System-wide middleware
├── paginations.py         # Global pagination classes
├── permissions.py         # Global permission classes
├── signals.py             # System-wide signals
├── tasks.py               # System-wide tasks
├── mixins.py              # System-wide mixins
└── version.py             # API version management
```


### 4. Logging Configurations ( `logging_config/` )

Separate logging configurations for different environments.

```bash

logging_config/
├── __init__.py
├── base.py                # Base logging configuration
├── development.py         # Development logging settings
├── env.py                 # Environment-specific logging variables
├── production.py          # Production logging settings
└── staging.py             # Staging logging settings
```

### 5. Tests Directory ( `tests/` )

Organized test structure mirroring the application structure.

```bash

tests/
├── test_applications/
│   └── test_feature/      # Tests for feature modules
│       ├── test_apis/
│       │   ├── test_serializers.py
│       │   ├── test_validators.py
│       │   ├── test_views.py
│       │   └── test_filters.py
│       ├── test_services/
│       ├── test_selectors/
│       ├── test_models/
│       └── test_event_handlers/
├── test_core/             # Tests for core modules
│   ├── test_authentication.py
│   ├── test_permissions.py
│   └── test_middleware.py
├── test_utilities/        # Tests for utilities
├── __init__.py
└── conftest.py            # Pytest fixtures and configuration
```

### 6. Utilities Directory ( `utilities/` )

Shared utility functions and helper modules.

```bash

utilities/
├── __init__.py
├── validators.py          # Custom validators
├── helpers.py             # Helper functions
├── decorators.py          # Custom decorators
├── constants.py           # System-wide constants
├── custom_types.py        # Custom type definitions
└── date_utils.py          # Date/time utilities
```

---


## Full Directory Structure


```bash

└── my-project/
    ├── applications/  # collection of features or applications
    │   ├── feature/  # ---> (app)
    │   │   ├── apis/  # API/Presentation layer
    │   │   │   ├── serializers/  # contains all feature specific serializers
    │   │   │   │   └── __init__.py
    │   │   │   ├── validators/  # contains all feature specific validators
    │   │   │   │   └── __init__.py
    │   │   │   ├── views/  # handles the HTTP requests & responses
    │   │   │   │   └── __init__.py
    │   │   │   ├── __init__.py
    │   │   │   ├── filters.py  # feature specific filters
    │   │   │   ├── permissions.py  # feature specific permissions
    │   │   │   └── urls.py  # this will contain the endpoints for this feature 1
    │   │   ├── clients/  # communicates with External services eg. HoduSoft, Zoho etc (optional)
    │   │   │   └── __init__.py
    │   │   ├── event_handlers/  # this contains feature specific signal
    │   │   │   └── __init__.py
    │   │   ├── exceptions/  # feature specific exception handling
    │   │   │   └── __init__.py
    │   │   ├── selectors/  # handles complex dB query logic
    │   │   │   └── __init__.py
    │   │   ├── jobs/  # this contains feature specific scheduled job or tasks
    │   │   │   ├── __init__.py
    │   │   │   └── tasks.py  # feature specific tasks
    │   │   ├── management/  # custom feature specific commands
    │   │   │   ├── commands/
    │   │   │   │   ├── __init__.py
    │   │   │   │   └── my_command.py
    │   │   │   └── __init__.py
    │   │   ├── migrations/  # contains all migrations files
    │   │   │   └── __init__.py
    │   │   ├── models/  # contains the model classes in this feature
    │   │   │   └── __init__.py
    │   │   ├── services/  # handles business rules and orchestration
    │   │   │   ├── __init__.py
    │   │   │   └── dto.py  # Data Transfer Objects
    │   │   ├── __init__.py
    │   │   ├── admin.py
    │   │   ├── apps.py
    │   │   └── constants.py  # feature specific constants
    │   └── __init__.py
    ├── configurations/  # contains the project configurations
    │   ├── library_configs/  # 3rd party configurations example: celery, aws etc
    │   │   ├── __init__.py
    │   │   ├── aws.py
    │   │   └── celery.py
    │   ├── settings/  # settings for different environments such as development, staging and production
    │   │   ├── __init__.py
    │   │   ├── base.py
    │   │   ├── development.py
    │   │   ├── production.py
    │   │   └── staging.py
    │   ├── __init__.py
    │   ├── asgi.py
    │   ├── env.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── core/  # contains all the system wide or global attributes
    │   ├── __init__.py
    │   ├── authentication.py  # global auth
    │   ├── constants.py  # system wide constants
    │   ├── context_processors.py  # system wide context processors (optional)
    │   ├── exceptions.py  # global exceptions
    │   ├── middleware.py   # system wide middleware (optional)
    │   ├── paginations.py  # global permissions
    │   ├── permissions.py  # global permissions
    │   ├── signals.py  # system wide signals (optional)
    │   ├── tasks.py  # system wide tasks (optional)
    │   ├── mixins.py  # system wide mixins (optional)
    │   └── version.py  # API version
    ├── logging_config/  # contains logging configurations
    │   ├── __init__.py
    │   ├── base.py
    │   ├── development.py
    │   ├── env.py
    │   ├── production.py
    │   └── staging.py
    ├── static/  # contains static JS, CSS, Images etc (optional)
    ├── templates/  # contains html files (optional)
    ├── tests/  # contains tests functionalities
    │   ├── test_applications/
    │   │   └── test_feature1/  # test all the modules in the feature per package
    │   ├── test_core/  # tests all the modules in core
    │   ├── test_utilities/
    │   ├── __init__.py
    │   └── conftest.py  # Pytest fixtures
    ├── utilities/  # shared or global utilities
    │   └── __init__.py
    ├── manage.py
    ├── pyproject.TOML
    ├── README.md
    └── .env


```