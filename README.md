📱 Modern Android Architecture – Dependency Guide

This repository demonstrates a modern Android development stack using Jetpack Compose, Clean Architecture, Dependency Injection, Networking, Database, and Testing frameworks.

The goal of this project is to show why each dependency is used and how it fits into a scalable Android architecture.

🏗 Architecture Overview

The project follows a robust, modern layered architecture:

Code snippet

graph TD

    A[UI - Jetpack Compose] --> B[ViewModel - State Management]
    
    B --> C[Repository - Business Logic]
    
    C --> D[Data Sources]
    
    D --> E[Network - Retrofit]
    
    D --> F[Local DB - Room]
    
Core Technologies

Jetpack Compose → Declarative UI

Hilt → Dependency Injection

Retrofit → Networking

Room → Local Persistence

Coroutines → Asynchronous Programming

Navigation Compose → In-app Navigation

MockK / JUnit / Espresso → Comprehensive Testing

📦 Dependency Explanation

Below is a breakdown of each dependency and its role in the ecosystem.

🔹 Core Android

androidx-core-ktx: Provides Kotlin extensions for Android APIs to ensure cleaner syntax and less boilerplate.

Kotlin
// Example: Concise SharedPreferences editing
prefs.edit { putString("name", "John") }

🔹 Lifecycle & Architecture

lifecycle-runtime-ktx: Adds lifecycle-aware Coroutine support, ensuring tasks stop when the Activity/Fragment ends.

lifecycle-viewmodel-compose: Bridges the gap between Compose and ViewModels.

Kotlin
val viewModel: MainViewModel = viewModel()

🔹 Jetpack Compose UI

compose-bom: A Bill of Materials that synchronizes versions for all Compose libraries (UI, Material, Tooling).

compose-ui: The core declarative UI toolkit.

compose-ui-graphics: Provides Canvas, custom drawing, and rendering tools.

compose-ui-tooling-preview: Enables the @Preview annotation for instant UI feedback in Android Studio.

🔹 Material Design & Activity

compose-material3: Implements Material Design 3 components (Buttons, Scaffolds, Cards).

activity-compose: Integrates Compose within standard Android Activities.

🔹 Dependency Injection (Hilt)

hilt-android: Automates object creation for cleaner architecture and better testability.

hilt-navigation-compose: Enables scoped ViewModel injection within a Navigation graph.

Kotlin
val viewModel: HomeViewModel = hiltViewModel()

🔹 Networking & Serialization

retrofit: A type-safe HTTP client for REST API communication.

converter-gson: Automatically maps JSON responses to Kotlin Data Classes.

kotlinx-serialization: A Kotlin-native way to convert objects to/from JSON.

🔹 Local Database (Room)

room-runtime: An abstraction layer over SQLite.

room-ktx: Adds Coroutine support for non-blocking database queries.

room-compiler: Annotation processor that generates the underlying implementation code.

🔹 Image Loading

Coil: A modern, Kotlin-first image loader optimized for Compose.

Glide: An alternative with powerful caching strategies for complex memory management.

📂 Project Structure

The project is organized by layer to support scalability and separation of concerns:

app/

 ├── di/                # Hilt Modules (Network, Database)
 
 ├── data/              # Implementation (API, DAO, Repository Impl)
 
 ├── domain/            # Business Logic (UseCases, Models)
 
 ├── ui/                # Presentation (Screens, ViewModels, Theme)
 
 └── util/              # Helpers & Extensions
 
 
🧪 Testing Frameworks
JUnit: Unit testing for business logic.

Espresso: Automated UI testing for traditional views.

Compose UI Test: Specialized library for testing Compose nodes.

MockK: Powerful library for mocking dependencies in a Kotlin-idiomatic way.
