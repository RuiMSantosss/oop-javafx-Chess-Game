# JavaFX Chess Engine: MVC@PA Architecture

## Executive Summary
This project represents a robust implementation of the classic Chess game, engineered to demonstrate advanced software design principles within the **Java** ecosystem.

Unlike standard game implementations, this system focuses heavily on **Architectural Integrity** and **Design Patterns**. It utilizes the **MVC@PA** (Model-View-Controller with Presenter Adapter) pattern to enforce a strict separation of concerns, ensuring that the game logic, user interface, and data layers remain decoupled and maintainable.

## Core Architecture & Design Patterns
The codebase serves as a practical case study for several industry-standard design patterns:

* **MVC@PA (Model-View-Controller-Presenter-Adapter):** The backbone of the application, separating the *JavaFX* interface from the *Core Logic*.
* **Factory Method:** Implemented to handle the polymorphic creation of chess pieces (King, Queen, Pawn, etc.) based on dynamic inputs or saved states.
* **Memento Pattern:** The engine behind the "Undo/Redo" system, allowing the game to capture and restore internal states without violating encapsulation.
* **Facade Pattern:** Utilized in the `ChessGameManager` to provide a simplified interface for the UI to interact with the complex subsystem of game rules.
* **Singleton:** Ensures a single, globally accessible instance for the `ModelLog` system.
* **Observer:** Facilitates reactive updates between the game model and the GUI.

## Feature Set
* **Complete Ruleset:** Full implementation of standard chess rules, including **Castling**, **En Passant**, and **Pawn Promotion**.
* **State Persistence:** Users can Save and Load games at any point via binary serialization.
* **Time Travel:** Robust Undo/Redo functionality powered by the Memento pattern.
* **Rich Feedback:** Includes move logging, error reporting, and audio cues (SoundManager).
* **Validation Engine:** Validates every move against board boundaries, piece capabilities, and "Check" states.

## Technical Stack
* **Language:** Java (JDK 21+)
* **GUI Framework:** JavaFX SDK 24
* **Testing:** JUnit 5
* **IDE:** IntelliJ IDEA

## Project Structure
The solution is modularized into distinct logical layers:

### 1. The Domain Model (Logic)
* `ChessGame`: The central brain managing turns and rule enforcement.
* `Board` & `Piece`: Representations of the grid and entities.
* `PieceType` / `PieceTeam`: Enumerations for strong typing.

### 2. State Management
* `ChessGameSerialization`: Handles the I/O for saving game states.
* `Caretaker` / `Originator` / `IMemento`: The implementation of the state restoration system.

### 3. User Interface (JavaFX)
* `BoardView`: The graphical rendering of the grid.
* `RootPane` & `TopMenuBar`: Layout managers.
* `ModelUI`: The adapter/mediator bridging the Model and the View.

---

## Quality Assurance (Testing)
Reliability is ensured through a comprehensive **JUnit 5** test suite covering critical logic:
* **Parameterized Tests:** Utilizing `@MethodSource` to validate high volumes of movement scenarios.
* **Factory Validation:** Ensuring the `ChessPieceFactory` correctly instantiates pieces based on string tokens.
* **Logic Verification:** Tests for checkmate detection, valid pathing, and board boundaries (`BoardTest`, `ChessGameTest`).

---

## Setup & Execution
**Prerequisites:** JavaFX SDK is required.

1.  **Clone** the repository.
2.  **Configure Libraries:** In your IDE (IntelliJ recommended), add the `JavaFX SDK` lib folder to your dependencies.
3.  **VM Options (Crucial):** You must add the following arguments to your Run Configuration to allow JavaFX modules to load:
    ```bash
    --module-path "/path/to/javafx-sdk/lib" --add-modules javafx.controls,javafx.media
    ```
4.  **Run** the main application class.

---

## Academic Context
This software was engineered as the capstone project for the **"Advanced Programming"** course (2024/2025).

**Team Size:** 2 Members
**Final Evaluation:** 9.6 / 10
