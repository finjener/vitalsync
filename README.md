# VitalSync

**VitalSync** is a graduation project that developed as a physiological monitoring application built with C++ and Qt. The primary goal of this project is to implement software engineering tools while developing a simple application to display vital data of patients.


## Overview

VitalSync is designed to acquire, process, and display real-time patient data, including various waveform visualizations (ECG, respiration) and numerical parameters (heart rate, SpO2, blood pressure).

## Project Architecture

The application follows a model-view-controller architecture with these core components:

- **Data Providers**: Acquire physiological data from various sources
- **Data Manager**: Coordinates data flow between providers and models
- **Models**: Store and process physiological data
- **Views**: Display data and handle user interactions
- **Configuration Manager**: Manages application settings

```
┌───────────────────┐     ┌────────────────────┐     ┌────────────────────┐
│  Data Providers   │     │   Data Manager     │     │      Models        │
│                   │     │                    │     │                    │
│  IDataProvider    │     │  IDataManager      │     │  IWaveformModel    │
│  DemoDataProvider ├────►│  - route data      ├────►│  IParameterModel   │
│                   │     │  - manage providers│     │                    │
└───────────────────┘     └────────────────────┘     └──────────┬─────────┘
          │                                                     │
          │               ┌─────────────────────────────────────┘
          │               │
          │               ▼
          │      ┌────────────────────┐                 ┌────────────────────┐
          │      │       Views        │                 │   Configuration    │
          │      │                    │                 │                    │
          │      │  IWaveformView     │                 │  ConfigManager     │
          └─────►│  IParameterView    │◄────Configure───│  - save settings   │
                 │                    │    Settings     │  - load preferences│
                 └────────────────────┘                 └────────────────────┘
```

## Application Lifecycle

1. **Initialization**: Set up the Qt application and load user settings.
2. **Component Creation**: Create the main window and configure the data manager.
3. **Data Acquisition**: Start acquiring data from the selected provider.
4. **Event Loop**: Handle user input and data updates.
5. **Shutdown**: Save settings and clean up resources.

## C++ Features Used

- **Interface-Based Design**: Abstract classes for loose coupling.
- **Smart Pointers**: Automatic memory management.
- **Namespaces**: Encapsulation of related items.
- **Containers and Algorithms**: Use of STL and Qt containers for data management.

## Qt Features Used

- **Signal-Slot Mechanism**: Loose coupling between components.
- **QObject Hierarchy**: Memory management and signal-slot support.
- **Custom Painting**: Render waveforms using QPainter.
- **Settings Management**: Use of QSettings for configuration storage.

## Building and Running

### Prerequisites

- Qt 5.15 or newer
- C++17 compatible compiler
- CMake 3.16 or newer

### Build Instructions

```bash
# Clone the repository
git clone https://github.com/finjener/vitalsync.git
cd vitalsync

# Create build directory
mkdir build && cd build

# Run CMake and build
cmake ..
make -j$(nproc)

# Run the application
./bin/VitalSync
```

Comments/documentation in the codebase are written doxygen compatible.

## Notes

This project developed as a learning tool and may contain unused or overly developed programming tools for educational purposes. The documentation is primarily for personal reference to understand the project later.

