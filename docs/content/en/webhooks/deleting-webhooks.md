---
title: 'Regitering Webhooks'
description: ''
category: 'Webhooks'
fullscreen: false 
position: 62
---

A webhook can be unergistered from a telegraph bot. This can be accomplished both programmatically and through an artisan command

## artisan command

You can unregister a webhook calling the `telegraph:unset-webhook` artisan command:

```shell
php artisan telegraph:unset-webhook
```

## programmatically

if you are implementing a custom bot management logic, you can unregister a webhok using the `TelegraphBot` model:

```php
/** @var DefStudio\Telegraph\Models\TelegraphBot $telegraphBot */

$telegraphBot->unregisterWebhook()->send();
```


### Pending updates

It may happen that there are pending message updates when deleting a webhook. By default they are kept in order to retrieve them through a manual polling. To drop these updates, use the `--drop-pending-updates` artisan command option

```shell
php artisan telegraph:unset-webhook --drop-pending-updates
```

or using a parameter inside the method call:

```php
$dropPendingUpdates = true;

$telegraphBot->unregisterWebhook($dropPendingUpdates)->send();
```
