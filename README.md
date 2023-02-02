# Status helper

## About

This provides real-time information about the availability of your services, enabling you to advise your users of your application's status. Utilizing SvelteKit, the app offers an intuitive interface for tracking the current and historical status of services, as well as upcoming maintenance schedules.

You can view a live example [here](https://gubareve-statusapp-demo.vercel.app/).

### Images

<img src="https://user-images.githubusercontent.com/24500411/216223631-c25f6c14-4c97-46fa-b496-cb8d291da272.png" width="300">
<img src="https://user-images.githubusercontent.com/24500411/216223656-d15f88e8-3eb1-437e-9c1d-25b0195103d6.png" width="300">

## Configuration

The configuration for the app is stored in the `/src/routes/status.json` file. The file consists of several fields, each of which determines a specific aspect of the app's functionality. 

### Services 
The `services` field holds an array of objects, each of which represents a service. Each service object has two properties:
- `name`: specifies the name of the service.
- `isOperational`: determines the current status of the service (online or not).

### Maintenance 
The `maintenance` field contains information about any upcoming maintenance schedules, with the following properties:
- `show`: determines whether the maintenance message is displayed or not.
- `message`: holds the text of the maintenance message.
- `time`: specifies the date and time of the maintenance.

### Incidents 
The `incidents` field holds an array of objects, each of which represents a past incident and includes the following properties:
- `date`: the date of the incident.
- `description`: the description of the incident.

### Config
The `config` field contains additional configuration options, such as the name of the app, specified by the following property:
- `appName`: the name of the app.


## Developing

Once you have installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

This will generate a static version of the site.

## Note

This app should be hosted on a platform that allows for automatic deployment on change of the `status.json` file. Then, all you have to do to add an incident/change uptime is edit the file on your source control system.
