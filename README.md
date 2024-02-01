create api/index.php in root folder

add below codes to index.php

```
<?php

require __DIR__ . '/../public/index.php';
```

create vercel.json in root folder and add below codes

```
{
    "version": 2,
    "functions": {
        "api/index.php": {
            "runtime": "vercel-php@0.6.0"
        }
    },
    "routes": [
        {
            "src": "/(.*)",
            "dest": "/api/index.php"
        }
    ],
    "outputDirectory": "public/build",
    "env": {
        "APP_NAME": "Vercel Laravel",
        "APP_ENV": "production",
        "APP_KEY": "*add key from .env*",
        "APP_DEBUG": "false",
        "APP_URL": "https://laravel-vercel.vercel.app",
        "VERCEL_DEMO_MODE": "true",
        "APP_CONFIG_CACHE": "/tmp/config.php",
        "APP_EVENTS_CACHE": "/tmp/events.php",
        "APP_PACKAGES_CACHE": "/tmp/packages.php",
        "APP_ROUTES_CACHE": "/tmp/routes.php",
        "APP_SERVICES_CACHE": "/tmp/services.php",
        "CACHE_DRIVER": "array",
        "LOG_CHANNEL": "stderr",
        "SESSION_DRIVER": "cookie",
        "VIEW_COMPILED_PATH": "/tmp/views",
        "SSR_TEMP_PATH": "/tmp/ssr",
        "NODE_PATH": "node"
    }
}
```
change prefix('api') to prefix('v1') or other prefer prefix in RouteServiceProvider

```
Route::middleware('api')
                ->prefix('v1')
                ->group(base_path('routes/api.php'));
```

now it is ready to add in github and deploy on vercel
