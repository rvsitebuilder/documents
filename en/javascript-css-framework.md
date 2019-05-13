# JavaScript and CSS Framework

RVsitebuilder user and admin interfaces are render independently.

## User interface
End-user interface is built on [UIKIT2](https://getuikit.com/v2/) framework. It changes dynamically according to the end-user choice of template on the admin area.

> {info} Soon, there will be a choice between `Bootstrap4`, `UIKIT2`, and `UIKIT3`.

## Admin interface
Admin interface is `platform agnostic`. If you generate app from developer app, admin layout suggest bootstrap4. But you can replace it with anything you want. If you use webpack to build your asset, simply build your own and remove the default one.

### `views/admin/layouts/app.blade.php` with bootstrap4:
```php
@extends('admin.layouts.master')

@section('leftmenu')
	@include('admin.includes.leftmenu', ['package_name' => "author/appname"])
@endsection

@push('package-styles')
    <!-- package-styles -->
    {{ style(@mixcdn('css/bootstrap.css', 'vendor/rvsitebuilder/wysiwyg')) }}    
    {{ style(@mixcdn('css/commons.css', 'vendor/rvsitebuilder/wysiwyg')) }} 
@endpush

@push('package-scripts')
    <!-- package-scripts -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.3.1/js/bootstrap.min.js"
    integrity="sha256-CjSoeELFOcH0/uxWu6mC/Vlrc1AARqbm/jiiImDGV3s=" 
    crossorigin="anonymous"></script>
@endpush
```

### `views/admin/layouts/app.blade.php` with UIKIT2:
```php
@extends('admin.layouts.master')

@section('leftmenu')
	@include('admin.includes.leftmenu', ['package_name' => "author/appname"])
@endsection

@push('package-styles')
    <!-- package-styles -->
    {{ style(@mixcdn('css/uikitv2.css', 'vendor/rvsitebuilder/wysiwyg')) }}   
    {{ style(@mixcdn('css/commons.css', 'vendor/rvsitebuilder/wysiwyg')) }} 
@endpush

@push('package-scripts')
    <!-- package-scripts -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/uikit/2.27.4/js/uikit.min.js" 
    integrity="sha256-LS0opR4j8nX0KQjO5pVVQkqXBw+qBk5lOg5XgJCXbYQ="
    crossorigin="anonymous"></script>     
@endpush
```


## jQuery 
Loaded as an external script on all pages, both admin and user interface. It has a global scope. You do not need to include it on your app. 

> {warning} Do not use `defer` on your script as it conflict with jQuery.


## Package-script Blade Stack
push(@package-script)
Endpush

## Wex

## Mex

## Passing PHP variables to JS through wex and mex

## Vue.js