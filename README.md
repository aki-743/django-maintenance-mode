# ライブラリ

```terminal
$ pipenv install django-maintenance-mode
```
# settings.py

## アクセス制限

```settings.py
# メンテナンス中でも管理サイトへアクセスできるようにする
MAINTENANCE_MODE_IGNORE_ADMIN_SITE = True

# メンテナンス中でもスーパーユーザーのみ通常サイトを見れるようにする
MAINTENANCE_MODE_IGNORE_SUPERUSER = True
```

## INSTALLED_APPS

```settings.py
INSTALLED_APPS = [
    ...
    'maintenance_mode',
    ...
]
```

## MIDDLEWARE

```settings.py
MIDDLEWARE = [
    ...
    'maintenance_mode.middleware.MaintenanceModeMiddleware',
]
```

## TEMPLATES

```settings.py
TEMPLATES = [
    {
        ...
        'DIRS': [
            os.path.join(BASE_DIR,'templates')
        ],
        ...
        'OPTIONS': {
            'context_processors': [
                ...
                'maintenance_mode.context_processors.maintenance_mode',
            ],
            ...
        },
    },
]
```

# メンテナンスページ

アプリディレクトリ直下に``templates``フォルダを作成し、``503.html``を作成

# メンテナンス

## 作動

```terminal
$ python manage.py maintenance_mode on
```

## キャンセル

```terminal
$ python manage.py maintenance_mode off
```
