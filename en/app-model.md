# App Model

- [Creating Model](#creating-model)
- [Accessing Model](#accessing-model)
- [Extending RVsitebuilder Default Models using Meta Table](#extending-rvsitebuilder-default-models-using-meta-table)

> {info} If you are not familiar with its concept. Check out the full [Laravel Eloquent ORM documentation](https://laravel.com/docs/5.8/eloquent) to get started.

## Creating Model

Create Laravel model file and keep it in your `app’s /src/Models` folder.

```php
/packages/vendor-name/project-name/
                    ├── src
                    │   ├── Models
                    │   │   └── MyTable.php
```

```php
namespace VendorName\ProjectName\Models;

class YourTable extends BaseModel
{
    protected $table = 'my_table';
    protected $fillable = ['name'];
}

```

## Accessing Model

Use your model namespace on your app and execute any Laravel Eloquent ORM syntax as usual.

```php
use VendorName\ProjectName\Models\YourTable;

```

## Extending RVsitebuilder Default Models using Meta Table

Ever want to add more data to `Users` table. Thanks to wonderful [Laravel-Metable](https://github.com/plank/laravel-metable) project to make it possible. You can extend RVsitebuilder default model without needing to adjust the database schema.

The following model are `metable`.

- Users
- CorePage
- BlogPost
- CoreSystemPage
- CoreGlobalWidget
- BlogCategory
- CoreFacebook
- CoreFooter
- CoreHeader
- CoreMenu
- CoreSeo
- CoreSidebar
- CoreSlug
- CoreTwitter
- Email
- EmailCategory
- ManageApp

Example Usage Metable.

```php

namespace Rvsitebuilder\Core\Models;

use Illuminate\Database\Eloquent\Model;
use Plank\Metable\Metable;

    class CoreGlobalWidget extends Model
    {
        use Metable;

        protected $table = 'core_global_widget';
        protected $fillable = [
                'app_id',
                'widget_name',
        ];
    }

```

Attach some metadata to an eloquent model.

```php
    // $setting = something
    $globalwidget = CoreGlobalWidget::updateOrCreate(
                    ['widget_name' => $widgetName],
                    [
                        'app_id' => $appID,
                        'widget_name' => $widgetName,
                    ]);
    $globalwidget->setMeta('global', $setting);

```

Retrieve the metadata from a model.

```php
    $widget = CoreGlobalWidget::find($id);
    $widget->getMeta('global');
```
