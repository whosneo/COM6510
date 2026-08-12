# Picture Manager (COM6510)

Android photo management app built for the University of Sheffield **COM6510** coursework. It lets you capture or import photos, store metadata locally, browse them on a gallery and map, search by keyword, and edit details.

## Features

- **Gallery** — grid of pictures on the home screen (`MainActivity`)
- **Camera / gallery import** — take photos or pick from the device (EasyImage)
- **Map view** — show photo locations on Google Maps; tap a marker for details
- **Search** — fuzzy keyword search over picture metadata
- **Edit info** — title, description and related fields; mini-map of the photo location
- **Delete** — remove pictures from the library
- **EXIF-aware display** — correct orientation when showing images

## Architecture

The app follows a simple **MVVM** layout:

| Layer | Package / classes |
|--------|-------------------|
| UI | Activities, adapters (`MainActivity`, `MapActivity`, …) |
| ViewModel | `PictureViewModel` |
| Repository | `PictureRepository` |
| Data | Room (`Picture`, `PictureDAO`, `PictureDatabase`) |

```
UI → ViewModel → Repository → Room DB
```

## Tech stack

- Java 8, Android SDK 28 (min SDK 23)
- AndroidX (AppCompat, RecyclerView, Lifecycle, Room, …)
- Google Play Services Maps & Location
- [EasyImage](https://github.com/jkwiecien/EasyImage) for capture / pick
- Material Components

## Project structure

```
COM6510/
├── app/
│   ├── src/main/java/uk/ac/shef/oak/com6510/
│   │   ├── database/          # Room entities & DAO
│   │   ├── repository/
│   │   ├── viewmodel/
│   │   └── *Activity.java     # UI screens
│   └── src/main/res/          # layouts, menus, values
├── docs/                      # generated JavaDoc
├── build.gradle
└── settings.gradle
```

## Prerequisites

- Android Studio (or SDK + Gradle compatible with AGP 3.3)
- Android device or emulator (API 23+)
- A **Google Maps API key** for map features

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/whosneo/COM6510.git
   cd COM6510
   ```

2. Open the project in Android Studio and let Gradle sync.

3. Configure Maps API key in `app/src/main/res/values/google_maps_api.xml` (or the string resource referenced by the manifest as `google_maps_key`).

4. Adjust signing paths in `app/build.gradle` if you use a local keystore (the sample path is machine-specific).

5. Run the `app` configuration on a device/emulator.

## Permissions

The app requests:

- `ACCESS_FINE_LOCATION` / `ACCESS_COARSE_LOCATION` — geotagging and map
- `WRITE_EXTERNAL_STORAGE` — store / access image files

Grant them when prompted on first launch.

## Documentation

Generated JavaDoc is under [`docs/`](docs/). Open `docs/index.html` in a browser.

## License

Coursework project for educational use. No separate license file is provided.
