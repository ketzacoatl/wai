## auto-update

A common problem is the desire to have an action run at a scheduled interval,
but only if it is needed. For example, instead of having every web request
result in a new `getCurrentTime` call, we'd like to have a single worker thread
run every second, updating an `IORef`. However, if the request frequency is
less than once per second, this is a pessimization, and worse, kills idle GC.

This library allows you to define actions which will either be performed by a
dedicated thread or, in times of low volume, will be executed by the calling
thread.

For original use case, see [yesod-scaffold issue #15](https://github.com/yesodweb/yesod-scaffold/pull/15).
