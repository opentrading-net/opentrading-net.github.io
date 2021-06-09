# Web User Interface State

- **Object Cache**: added as a singleton service 
    - e.g. ```services.AddSingleton<ObjectCache>();```
    - Injected into the **Transaction Service** by Blazor and used by the **Object Store Transaction**
- **Transaction Service**: added as a scoped service - so a single instance per user
    - What happens on the refresh of browser: https://stackoverflow.com/questions/63058879/blazor-server-scoped-inititialized-again-on-refreshing-the-page says new circuit so new service
- **Session Management**: holds the current and default session. 
    - Created by the **Transaction Service** => singleton scope not browser tab specific
- **Current Session**: what do we want?
    - Common session per user/browser - not as good
    - Session per linked sets of tabs and popups - yes
    - How : could just use URL parameter and cause a refresh with a new parameter on session change? see navigationManager.NavigateTo(navigationManager.Uri, forceLoad: true)
- **Tesseract Component Base** is the base of all components and is injected **Transaction Service**

=> get a web session management object per page and give to transaction service...