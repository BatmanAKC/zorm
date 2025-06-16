# Zorm: A Zig ORM with Custom Schema Support 🚀

![Zorm Logo](https://img.shields.io/badge/Zorm-v1.0.0-brightgreen)  
[![Releases](https://img.shields.io/badge/releases-latest%20release-blue)](https://github.com/BatmanAKC/zorm/releases)

---

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Supported Databases](#supported-databases)
- [Custom Schema Support](#custom-schema-support)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Introduction

Welcome to **Zorm**, a powerful Object-Relational Mapping (ORM) library designed for the Zig programming language. Zorm simplifies database interactions by allowing developers to work with objects instead of raw SQL queries. With custom schema support, Zorm adapts to various database structures, making it flexible for different projects.

You can find the latest releases of Zorm [here](https://github.com/BatmanAKC/zorm/releases). Make sure to download and execute the appropriate files for your setup.

---

## Features

- **Easy to Use**: Zorm offers a simple API for database operations.
- **Custom Schema Support**: Adapt your database structure without hassle.
- **Multiple Database Support**: Works with PostgreSQL, SQLite, and MongoDB.
- **Active Development**: Regular updates and improvements based on user feedback.
- **Lightweight**: Minimal overhead, ensuring your application runs smoothly.

---

## Installation

To get started with Zorm, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/BatmanAKC/zorm.git
   cd zorm
   ```

2. **Build the Project**:
   ```bash
   zig build
   ```

3. **Download the Latest Release**:
   Visit the [Releases](https://github.com/BatmanAKC/zorm/releases) section to download the latest version. Follow the instructions provided for installation.

4. **Run the Example**:
   ```bash
   zig run example.zig
   ```

---

## Usage

Using Zorm is straightforward. Here’s a quick example to illustrate how to connect to a database and perform basic operations.

### Connecting to a Database

```zig
const std = @import("std");
const zorm = @import("zorm");

pub fn main() !void {
    const db = try zorm.connect("postgres://user:password@localhost:5432/mydb");
    defer db.close();

    // Your database operations here
}
```

### Creating a Table

```zig
try db.createTable("users", .{
    .name = "VARCHAR(100)",
    .email = "VARCHAR(100) UNIQUE",
});
```

### Inserting Data

```zig
try db.insert("users", .{
    .name = "John Doe",
    .email = "john@example.com",
});
```

### Querying Data

```zig
const users = try db.query("SELECT * FROM users");
for (users) |user| {
    std.debug.print("User: {}\n", .{user.name});
}
```

---

## Supported Databases

Zorm supports a variety of databases to suit your needs:

- **PostgreSQL**: A powerful, open-source object-relational database.
- **SQLite**: A lightweight database ideal for smaller applications.
- **MongoDB**: A NoSQL database for flexible data storage.

Each database has its own configuration requirements. Refer to the documentation for specifics on setting up each type.

---

## Custom Schema Support

Zorm’s custom schema support allows you to define your database structure according to your application’s needs. This flexibility means you can easily adapt to changes in your data model without extensive rewrites.

### Defining a Custom Schema

You can define a custom schema by creating a configuration file. Here’s an example:

```zig
const schema = .{
    .users = .{
        .name = "VARCHAR(100)",
        .email = "VARCHAR(100) UNIQUE",
    },
    .posts = .{
        .title = "VARCHAR(255)",
        .content = "TEXT",
        .user_id = "INTEGER",
    },
};
```

This schema can then be used to create tables and enforce relationships between them.

---

## Contributing

We welcome contributions from the community! If you’d like to help improve Zorm, please follow these steps:

1. **Fork the Repository**: Click the "Fork" button at the top right of the repository page.
2. **Create a Branch**: Use a descriptive name for your branch.
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make Changes**: Implement your changes or features.
4. **Commit Your Changes**:
   ```bash
   git commit -m "Add a feature"
   ```
5. **Push to Your Branch**:
   ```bash
   git push origin feature/your-feature-name
   ```
6. **Create a Pull Request**: Go to the original repository and submit a pull request.

We appreciate your contributions and feedback!

---

## License

Zorm is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

---

## Contact

For questions, suggestions, or feedback, please reach out to the maintainer:

- **GitHub**: [BatmanAKC](https://github.com/BatmanAKC)
- **Email**: batmanakc@example.com

Feel free to connect with us and share your experiences using Zorm!

---

For more details, updates, and to explore the latest features, check the [Releases](https://github.com/BatmanAKC/zorm/releases) section. Download the latest version and start building your applications with ease!