---
layout: post
title:  "Blazor"
date:   2022-05-01 09:00:00 +0100
categories: .Net
---

* Blazor comes in 2 flavours - Blazor Server and Blazor Web Assembly
* Blazor Server executes .Net code on the server side and generates html and events that is sent to the browser through Signal-R.
* Blazor Web Assembly functions like a SPA whereby the browser hosts a .Net runtime that executes .Net dll and renders the UI.

#### Push notifications
* Calling `StateHasChanged` indicates to the blazor engine that a state needs to the reflected on the client and will perform the diff mechanim.
* The update to the HTML gets sent via signal r to the client.
* `StateHasChanged` is typically used for updates that are outside of the blazor lifecycle flow (eg OnInitialized or OnParametersSetAsync)
* Blazor event handling has it's own mechanism of updating the UI and no required to explicitly call `StateHasChanged`.
* In cases where a logic is running outside of the Blazor synchronization context, it is necessary to call `StateHasChanged` within an `InvokeAsync` block:

{% highlight csharp linenos %}
InvokeAsync(() =>
{
    StateHasChanged();
});
{% endhighlight %}