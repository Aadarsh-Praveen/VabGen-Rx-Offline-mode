<p align="center">
  <img src="./vabgen_logo.png" alt="VabGenRx Logo" width="250"/>
</p>

# VabGen-Rx-Offline-mode 🏥📴

**VabGen-Rx Offline Mode** is a specialized version of the VabGen-Rx platform, engineered specifically for deployment in rural areas and remote regions where internet access is unreliable or non-existent. This repository ensures that critical healthcare tools and diagnostic utilities remain functional on local hardware.

## Purpose
In rural healthcare settings, a lack of connectivity can be a barrier to life-saving technology. This "Offline Mode" serves as a local-first solution, allowing healthcare workers to:
- Access patient records and diagnostic data without a live connection.
- Record new data locally with zero latency.
- Synchronize data automatically once the device reaches an area with internet access.

## Key Features
- **Offline-First Architecture:** Built using Service Workers and PWAs (Progressive Web Apps) to ensure the app loads even without a network.
- **Local Storage Management:** Utilizes IndexedDB/SQLite for robust local data persistence.
- **Smart Synchronization:** A background sync engine that handles data conflicts and pushes updates to the cloud whenever a connection is restored.
- **Low-Resource Requirement:** Optimized to run on low-end laptops, tablets, or Raspberry Pi devices often used in rural clinics.

## Installation & Setup

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/Aadarsh-Praveen/VabGen-Rx-Offline-mode.git](https://github.com/Aadarsh-Praveen/VabGen-Rx-Offline-mode.git)
   cd VabGen-Rx-Offline-mode
   ```

2. **Install Dependencies:**
   ```bash
   npm install
   ```

3. **Configure Environment:**
   Rename `.env.example` to `.env` and configure your local storage parameters and the primary API synchronization endpoint.

4. **Build for Production:**
   ```bash
   npm run build
   ```

5. **Start Local Server:**
   ```bash
   npm run start
   ```

## Synchronization Workflow
1. **Action:** User saves a prescription or diagnostic report.
2. **Store:** The app saves the entry to the local `IndexedDB`.
3. **Queue:** The `Service Worker` adds the task to a background sync queue.
4. **Push:** When `navigator.onLine` returns true, the app sends the queued data to the central VabGen-Rx server.

## Project Structure
- `/src/services/offline-store.js` - Logic for local data persistence.
- `/src/workers/sync-worker.js` - Service worker for background data synchronization.
- `/public/manifest.json` - PWA configuration for "Add to Home Screen" support.

## Contributing
We encourage developers to help optimize the synchronization logic or improve the UI for low-light rural environments. Please open an issue or submit a pull request.

## License
This project is licensed under the MIT License.

