<blockquote class="important">This documentation is for Magento 1.x. For Magento 2.x, see <a href="https://nickolasburr.github.io/magento/extensions/2.x/cloudpubsubeventanalytics/latest/">here</a>.</blockquote>

## Installation Guide

This guide explains how to install Cloud Pub/Sub Event Analytics and its dependencies.

### Requirements

+ [Composer](https://getcomposer.org)
+ [modman](https://github.com/colinmollenhour/modman) (Recommended)

### Dependencies

Cloud Pub/Sub Event Analytics relies on components from the [Google Cloud PHP](https://googlecloudplatform.github.io/google-cloud-php) library for Pub/Sub communication.
Listed below are those dependencies and each dependency requirements, all of which are handled by Composer.

+ [google/cloud-pubsub](https://packagist.org/packages/google/cloud-pubsub)
    - [google/cloud-core](https://packagist.org/packages/google/cloud-core)
    - [google/gax](https://packagist.org/packages/google/gax)

Cloud Pub/Sub Event Analytics is pre-packaged with the necessary Composer files, therefore no additional configuration should be needed to install the dependencies.

### Getting Started

Make sure you've downloaded your copy of the extension archive. If you have not yet purchased the extension, you can do so at the following locations:

+ [https://store.nickolasburr.com/extensions/magento-1-x/analytics/cloud-pubsub-event-analytics.html](https://store.nickolasburr.com/extensions/magento-1-x/analytics/cloud-pubsub-event-analytics.html)
+ [http://marketplace.magento.com/nickolasburr-nickolasburr-cloudpubsubeventanalytics.html](http://marketplace.magento.com/nickolasburr-nickolasburr-cloudpubsubeventanalytics.html)

Next, we'll show how to install the extension via `modman` and manually.

#### modman

```
cd /var/www                                                           # Replace with the Magento root directory
modman init                                                           # Only run if you haven't initialized modman yet.
mkdir -p .modman/NickolasBurr_CloudPubSubEventAnalytics && \
tar -C .modman/NickolasBurr_CloudPubSubEventAnalytics \
    -xzf /path/to/NickolasBurr_CloudPubSubEventAnalytics-1.0.0.tgz
```

The extension archive does not contain a `modman` file, but one is available [here](https://docs.nickolasburr.com/magento/extensions/1.x/cloudpubsubeventanalytics/latest/examples/modman).
Run the following to add the `modman` file to the extension root directory:

```
curl -fsL https://docs.nickolasburr.com/magento/extensions/1.x/cloudpubsubeventanalytics/latest/examples/modman \
     > .modman/NickolasBurr_CloudPubSubEventAnalytics/modman
```

Lastly, deploy the updates:

```
modman deploy NickolasBurr_CloudPubSubEventAnalytics
```

#### Manual

```
# Replace /var/www with the Magento root directory.
cd /var/www
mkdir -p /tmp/NickolasBurr_CloudPubSubEventAnalytics && \
tar -C /tmp/NickolasBurr_CloudPubSubEventAnalytics \
    -xzf /path/to/NickolasBurr_CloudPubSubEventAnalytics-1.0.0.tgz
rsync -Pahmvz --stats \
              --exclude="package.xml" /tmp/NickolasBurr_CloudPubSubEventAnalytics/* ./
rm -rf /tmp/NickolasBurr_CloudPubSubEventAnalytics
```

### Composer

After the extension files are installed, we need to install the library dependencies via Composer.

```
# Replace /var/www with the Magento root directory.
cd /var/www/lib/NickolasBurr
composer install --no-dev
```

The Composer file is configured to install modules under `lib/NickolasBurr` instead of `lib/NickolasBurr/vendor`. This is done to make compatibility with Magento 1.x easier.

### Wrapping It Up

Before attempting to configure the extension, make sure to clear the configuration cache, and, if any admin sessions are open, log out and log back in.