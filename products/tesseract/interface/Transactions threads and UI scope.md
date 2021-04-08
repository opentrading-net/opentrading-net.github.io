# Transactions, threads and UI scope

Blazor has a concept of scoped services (see [Blazor dependency injection](https://docs.microsoft.com/en-us/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0&pivots=server)) where essentially a scope is the same as a browser tab.

We want to manage Tesseract trasnactions at the scope level so we have a TransactionService injected into the UI components as a scoped service.

The Tesseract object store, type compiler etc. hold the current transaction on a thread but a brower tab will have multiple components with async rendering which means it will use multiple threads; moreover those threads will be reused across tabs.

So we need to ensure that a thread doesn't hold transaction information after rendering is complete even if the scope does still have an open transaction.

