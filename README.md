go-retryablehttp
================

Forked from hashicorp/go-retryablehttp

Updated to allow the latest response body to be saved and accessible after client.Do() finishes. This helps is you need to read/inspect the body in a CheckRetry function, but then still want access to the body after Do() completes.

Example use case: A specific response code is provided in a body when an auth token has expired from system A. In this case you want to drop out of the retry mechanism to obtain a new token as retrying with the old one is pointless. However, having read the body already the reader is empty when Do() completes so the calling function cannot determine whether a new token is required or not.
