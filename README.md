📱 Modern Android Architecture – Dependency Guide

This repository demonstrates a modern Android development stack using Jetpack Compose, Clean Architecture, Dependency Injection, Networking, Database, and Testing frameworks.

The goal of this project is to show why each dependency is used and how it fits into a scalable Android architecture.

🏗 Architecture Overview

The project follows a modern Android architecture stack:

UI (Compose)
   ↓
ViewModel (State Management)
   ↓
Repository (Business Logic)
   ↓
Data Sources
   ├── Network (Retrofit)
   └── Local Database (Room)

Core technologies used:

Jetpack Compose → UI
Hilt → Dependency Injection
Retrofit → Networking
Room → Local database
Coroutines → Async programming
Navigation Compose → Navigation
MockK / JUnit / Espresso → Testing
📦 Dependency Explanation

Below is a breakdown of each dependency and why it is required.

Core Android
androidx-core-ktx

Provides Kotlin extensions for Android APIs.

Benefits:

Cleaner Kotlin syntax
Less boilerplate
Extension functions

Example:

prefs.edit {
    putString("name", "John")
}
Lifecycle & Architecture
lifecycle-runtime-ktx

Adds lifecycle aware coroutine support.

Example:

lifecycleScope.launch {
    viewModel.loadData()
}

This ensures tasks stop when Activity/Fragment lifecycle ends.

lifecycle-viewmodel-compose

Allows Jetpack Compose to access ViewModels.

Example:

val viewModel: MainViewModel = viewModel()
Jetpack Compose UI
compose-bom

BOM (Bill Of Materials) ensures all Compose libraries use compatible versions.

Instead of manually managing versions for:

compose-ui
compose-material
compose-tooling

Compose BOM keeps them synchronized.

compose-ui

Core UI toolkit used to build Android UI declaratively.

Example:

Text("Hello World")
compose-ui-graphics

Provides graphics APIs:

Canvas
Custom drawing
Shapes
Rendering tools

Example:

Canvas(modifier = Modifier.size(100.dp)) {
    drawCircle(Color.Red)
}
compose-ui-tooling

Used for debugging Compose layouts inside Android Studio.

Used during development only.

compose-ui-tooling-preview

Enables @Preview annotation.

Example:

@Preview
@Composable
fun PreviewHome() {
    HomeScreen()
}
compose-ui-test-junit4

Testing library for Compose UI tests.

Example:

composeTestRule.onNodeWithText("Login").assertExists()
Material Design
compose-material3

Provides Material Design 3 UI components.

Examples:

Button
Card
Scaffold
TopAppBar
NavigationBar

Example:

Button(onClick = {}) {
    Text("Login")
}
Activity Integration
activity-compose

Allows Compose to run inside Android Activities.

Example:

setContent {
    MyApp()
}
Dependency Injection
Hilt

Hilt is used for Dependency Injection to manage object creation automatically.

Benefits:

Cleaner architecture
Testability
Scalable code

Example:

@HiltViewModel
class HomeViewModel @Inject constructor(
    private val repository: UserRepository
)
hilt-android-compiler

Annotation processor that generates the dependency graph.

Required for:

@Inject
@Module
@InstallIn
hilt-navigation-compose

Allows ViewModel injection in Compose navigation.

Example:

val viewModel: HomeViewModel = hiltViewModel()
Networking
Retrofit

Type-safe HTTP client used for REST API communication.

Example:

@GET("users")
suspend fun getUsers(): List<User>
converter-gson

Converts JSON responses into Kotlin objects.

Example:

{
 "name": "John"
}

Converted into:

User(name="John")
Local Database
Room

Official Android database library built on SQLite.

Components:

Entity
DAO
Database

Example:

@Dao
interface UserDao {
    @Query("SELECT * FROM users")
    suspend fun getUsers(): List<User>
}
room-ktx

Adds Kotlin coroutine support for Room.

Allows:

suspend fun getUsers()
room-compiler

Annotation processor that generates database implementation code.

Image Loading
Coil

Modern Kotlin-first image loading library optimized for Compose.

Example:

AsyncImage(
    model = imageUrl,
    contentDescription = null
)
Glide

Alternative image loading library with strong caching support.

Used for:

Network images
Memory caching
Disk caching
Navigation
Navigation Compose

Handles screen navigation in Jetpack Compose.

Example:

NavHost(navController, startDestination = "home")

Supports:

Deep links
Navigation arguments
Back stack handling
Asynchronous Programming
Kotlin Coroutines

Used for background tasks and concurrency.

Examples:

Network requests
Database queries
Background processing

Example:

viewModelScope.launch {
    repository.getUsers()
}
Serialization
Kotlinx Serialization

Converts Kotlin objects ↔ JSON.

Example:

@Serializable
data class User(val name: String)
Testing
JUnit

Unit testing framework used for testing business logic.

Espresso

UI testing framework used for automated UI testing.

Example:

onView(withId(R.id.login)).perform(click())
MockK

Mocking library used to simulate dependencies during tests.

Example:

val repo = mockk<UserRepository>()
Plugins Used
Android Application Plugin

Builds the Android application module.

Kotlin Android Plugin

Adds Kotlin support for Android.

Compose Plugin

Required for Jetpack Compose compilation.

Hilt Plugin

Enables dependency injection setup.

KSP

Kotlin Symbol Processing used for faster annotation processing.

Used by:

Room
Hilt
Serialization
📂 Project Structure Example
app/
 ├── di/
 │    ├── NetworkModule
 │    └── DatabaseModule
 │
 ├── data/
 │    ├── api
 │    ├── database
 │    └── repository
 │
 ├── domain/
 │    └── usecase
 │
 ├── ui/
 │    ├── screens
 │    └── viewmodel
🚀 Purpose of This Repository

This repository serves as a reference implementation for modern Android architecture, including:

Clean Architecture principles
Modern Android libraries
Scalable dependency setup
Production-ready structure
📚 Learning Goals

This project helps developers understand:

Modern Android architecture
Dependency management
Compose UI development
Dependency Injection
Networking & database integration
Testing strategies
