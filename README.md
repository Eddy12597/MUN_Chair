# MUN_Chair
A JavaFX Based Model UN Chairing Program

## What is Model UN?

Model United Nations (Model UN or MUN) is an educational simulation in which students role-play as delegates to the United Nations and simulate UN committees. Participants research countries, debate global issues, draft resolutions, and negotiate with others to solve real-world problems.

### UNA-USA Style

The UNA-USA (United Nations Association of the USA) style is the most widely used format for Model UN conferences in the United States. It emphasizes parliamentary procedure, formal debate, and resolution writing.

#### How This Program Models UNA-USA Committees

This program provides a structured way to manage a Model UN committee, with the following core components:

- **Committee Logic:**  
  The `Committee` class is a singleton that manages global committee state, including the list of delegates, resolutions, topics, and amendments. It supports both regular and Security Council (SC) modes, with logic to identify permanent members and manage speech lengths.

- **Delegates:**  
  Each delegate is represented by the `Delegate` class, which tracks their name, performance statistics (speeches, POIs, amendments), and status (present, present and voting, main submitter). JavaFX properties are used for UI binding, while serialization logic ensures compatibility with JSON for saving/loading committee state.

- **Performance Tracking:**  
  The `Performance` class records quantitative metrics for each delegate, such as the number of speeches, POIs, and amendments. These are weighted and combined into a score, which can be used for awards or analytics.

- **Resolutions and Topics:**  
  Resolutions are managed by the `Resolution` class, which tracks the main submitter, co-submitters, and a list of clauses. Each resolution is associated with a topic, managed by the `ResolutionTopic` class. The code supports adding, removing, and searching for resolutions and topics, with logic for swapping resolution numbers and maintaining order.

- **Amendments:**  
  Amendments are tracked globally and can be added or removed from the committee. Each amendment is associated with a unique ID and can be searched or listed.

- **Serialization:**  
  The committee state (delegates, resolutions, topics, amendments) can be saved to and loaded from a JSON file. This allows persistent storage and easy recovery of committee progress.

- **Logging:**  
  The program uses Java's logging framework to record events, warnings, and errors to a log file (`app.log`). This helps with debugging and tracking committee activity.

- **User Interface:**  
  The application is built with JavaFX, providing a graphical interface for chairs to manage the committee, track delegate performance, and facilitate debate.

#### Technical Features

- **Thread-Safe Collections:**  
  The code uses thread-safe collections (e.g., `CopyOnWriteArrayList`, synchronized lists) to ensure safe concurrent access to resolutions and amendments.

- **Custom Sorting:**  
  Resolutions are sorted using insertion sort for small lists and Java's default sort for larger lists, optimizing performance.

- **Utility Methods:**  
  Helper methods are provided for converting between Roman numerals and integers, useful for clause and sub-clause indexing.

- **Extensibility:**  
  The code is modular, making it easy to add new features such as new types of motions, advanced analytics, or integration with external systems.

---

This program aims to help chairs manage UNA-USA style committees efficiently, track delegate performance, and facilitate the flow of debate and documentation, with a focus on robust data management and extensible architecture for programmers.
