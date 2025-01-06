Since cached files live for the TTL, if you update the origin with new files, you may wish to send a cache invalidation to all edge locations for those files. Bypassing the TTL.

Now when a user requests those files, the edge location requests the fresh file from the origin because the cache it has is invalidated.

You can invalidate the entire cache or specific paths, like /images.

