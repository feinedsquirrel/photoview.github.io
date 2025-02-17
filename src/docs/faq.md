---
title: FAQ
group: root
---

## Move cache to another hard drive?

Yes you can. If you are running Photoview using docker-compose, change/add the volume mount that points to the cache to bind it to a path on your other hard drive.

```yml
volumes:
  # Change this:
  - api_cache:/app/cache
  # To this:
  - /path/to/hard-drive/photoview_cache:/app_cache
```

If you are not using Docker, simply set the `PHOTOVIEW_MEDIA_CACHE` environment variable to the desired path. E.g.:
- Set the variable in `.env`,
- Or alternatively, `export PHOTOVIEW_MEDIA_CACHE=/path/to/hard-drive/photoview_cache`

## My PHOTOVIEW_MEDIA_CACHE is very large! Is it safe to delete it?

The size of the media cache will scale with the size of your photo library, and as such it can become very large.
If you delete it, it will be recreated if you continue to use Photoview.
As such it is not advisable to delete the cache if you are still using Photoview, unless, perhaps, if you are significantly changing the library of photos on disk.
If you want to permanently uninstall Photoview, then yes, feel free to remove/delete the directory so as not to waste storage space.
In this case, you will also likely want to remove your database.

## I click "Scan All" but nothing happens

If you are using Docker, make sure that your media is properly mounted. If you are unsure about that see [Setup with Docker](/docs/installation-docker/).

To troubleshoot this, you can enter the container and check that the media is present.
To do this execute the following command `docker-compose exec photoview /bin/bash`, then list the mounted directory with `ls /photos`.

## Where do I find logging information

Navigate to the directory where your `docker-compose.yml` file lies, and execute `docker-compose logs`.
