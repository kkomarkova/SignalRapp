# SignalRapp
WebAssembly Blazor chatting app, thanks to this example I have learned how to
- Create a WebAssembly Blazor app<br/>
- Add the SignalR client library<br/>
- Add SignalR services and endpoint for the  SignalR hub<br/>
- Add Razor component code for chat<br/>

<img width="736" alt="signalr-blazor-finished" src="https://user-images.githubusercontent.com/58290791/118115867-ca6fab80-b3e9-11eb-825c-d6e2f61f5bfd.png"> <br/>
## Requirements
To run this app without any issues you need to have  **Visual Studio 2019 16.8** or later and  **.NET 5.0 SDK** or later installed.
## Interesting part of the code
### SignalR client library
To be able to use SignalR for the client, we need to add NuGet Package ```Microsoft.AspNetCore.SignalR.Client``` from ```nuget.org``` source by right-clicking on ```SignalRapp.Client```.
### SignalR Hub
**SignalR hub** enables us to call methods on connected clients from the server. In the server code, we define methods, that are called by client and In the client code, we define methods that are called from the server. SignalR takes care of everything behind the scenes that makes real-time client-to-server and server-to-client communications possible.
```yml
using System.Threading.Tasks;
using Microsoft.AspNetCore.SignalR;

namespace BlazorWebAssemblySignalRApp.Server.Hubs
{
    public class ChatHub : Hub
    {
        public async Task SendMessage(string user, string message)
        {
            await Clients.All.SendAsync("ReceiveMessage", user, message);
        }
    }
}
```
Under the Server project part, we created folder called **Hubs** and we added class **Chathub.cs**
