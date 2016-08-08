# Beacon API

Beacons(one-way requests) are used for sending reports on events, state updates, and analytics to servers. Beacons are also responsible for sending critical application and measurement information. Because beacons should not compete with higher priority tasks such as fetching resources and running animations, web developers are forced to use performance costly methods to deliver this critical information.

The Beacon API allows for an efficient way to send information to a server in the cloud via the [sendBeacon](https://msdn.microsoft.com/library/mt668926) method. The `sendBeacon` method is fully asynchronous and does not need to process a response. `sendBeacon` avoids accidental slowdowns by not processing a response when it doesn't need to be processed.



## Uses

Due to `sendBeacon` being asynchronous and non-blocking, `sendBeacon` is useful for a number of scenarios where XHR/fetch is commonly used today while forgoing performance tradeoffs.
Some key scenarios where `sendBeacon` can be used to gather telemetry include:
- When important actions in the browser are completed.
- When `onUnload`/`onBeforeUnload` are fired.
- When a page’s state changes from visible to hidden.
- When an uncaught exception handler occurs.

Another key use of the `sendBeacon` method is giving developers a way to gather time-critical information without hurting the user experience. Before `sendBeacon` was implemented, developers would instead block requests by creating synchronous `XMLHttpRequest`s and implementing techniques that block the browser from making time-critical operations like clicks and other handlers,



## Example

The following example sends a beacon to a server upon page visibility change. Once a tab goes from visible to hidden (or vice versa) the following JavaScript attempts to send some sample beacon data to the server.
For this example, the data is the timestamp of the send. The server will receive the data and log the timestamp of reception.


In the situation that the Beacon API is not supported, asynchronous `XMLHttpRequest` is used.


```javascript
// Flag to determine if beacon has been used
var usedBeacon = false;

// Upon visibilitychange, send request to the server
document.addEventListener('visibilitychange', function(event) {

   // Use sendBeacon if supported
   if(navigator.sendBeacon) {
      usedBeacon = sendBeacon();
   }

   // Fallback to async XMLHttpRequest if beacon is not supported
   if(!usedBeacon) {
      sendXhr();
   }

   // Re-render the page with the latest available roundtrip data (there’s no guarantee this last one has returned yet)
   location.reload();
});

// Sends a beacon with the current time and returns true
function sendBeacon() {
   console.log("Sending beacon");
   navigator.sendBeacon('/data', Date.now().toString());
   return true;
}

// Sends an XMLHttpRequest with the current time
function sendXhr() {
   console.log("Falling back to async xhr");
   var xhr = new XMLHttpRequest();
   xhr.open("POST", "/data", true); // async
   xhr.setRequestHeader("Content-Type", "text/plain;charset=UTF-8");
   xhr.send(Date.now().toString());
}

```

![spec](NavigatorBeacon)

## API reference
[Navigator.sendBeacon](https://msdn.microsoft.com/library/mt668926)

[WorkerNavigator.sendBeacon](https://msdn.microsoft.com/library/mt668925)

## Specification
[Beacon](http://www.w3.org/TR/beacon/)
