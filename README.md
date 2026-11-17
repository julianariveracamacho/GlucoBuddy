# GlucoBuddy

GlucoBuddy is a diabetes support prototype by Juliana Rivera Camacho. It brings recurring tasks into one place, including medication logging, supply tracking, recipes, and a wishlist.

| Version | Source | Stack |
| --- | --- | --- |
| Web V2 | [web/](web/) | HTML, CSS, JavaScript, and browser localStorage |
| Mobile V2.1 | [mobile/](mobile/) | React Native and Expo |

## Try the web prototype

From the repository root, run:

```sh
python3 -m http.server 8080 --directory web
```

Open [localhost:8080](http://localhost:8080). Try marking a sample medication as taken, exporting the event history as CSV, or updating a supply order status. Use fictional data for demos. Browser reminders depend on notification permissions and an open page.

## Mobile prototype

See the [Expo setup and testing notes](mobile/README.md) for the mobile draft.

## Project status

GlucoBuddy is a portfolio prototype for organizing daily routines. It uses local device storage and is intended for demonstration with fictional data.
