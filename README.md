## Tenancy for Laravel

A simple app demonstrating [stancl/tenancy](https://tenancyforlaravel.com) package on a simple Vue + Inertia app (Breeze starter kit).

Launch a tinker shell and create two tenants.

```php
Tenant::create(['id' => 'foo'])->domains()->create(['domain' => 'foo.localhost']);
Tenant::create(['id' => 'bar'])->domains()->create(['domain' => 'bar.localhost']);
```

Create models for a tenant.

```php
Tenant::find('foo')->run(fn () => User::factory(10)->create());
```
