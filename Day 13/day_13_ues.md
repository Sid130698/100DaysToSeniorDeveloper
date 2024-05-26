## Interview Questions

### # What is JDBC and why is it used?

* JDBC (Java Database Connectivity) is an API in Java that allows Java programs to interact with relational databases. It is used to execute SQL queries, update statements, and retrieve results from a database.

### # What are the main components of the JDBC API?

* The main components of the JDBC API are:
  * DriverManager: Manages a list of database drivers.
  * Connection: Represents a connection to a specific database.
  * Statement: Used to execute SQL queries.
  * ResultSet: Represents the result set of a query.
  * SQLException: Handles SQL errors and exceptions.

### # Can you explain the steps to connect to a database using JDBC?

* The steps to connect to a database using JDBC are:
  1. Load the JDBC driver.
  2. Establish a connection using DriverManager.
  3. Create a Statement object to execute SQL queries.
  4. Execute the query and process the ResultSet.
  5. Close the connection.

### # What is a JDBC driver and what are its types?

* A JDBC driver is a software component that enables Java applications to interact with a database. There are four types of JDBC drivers:
  1. Type-1: JDBC-ODBC Bridge Driver
  2. Type-2: Native-API Driver
  3. Type-3: Network Protocol Driver
  4. Type-4: Thin Driver

### # How do you perform CRUD operations using JDBC?

* To perform CRUD operations using JDBC:

  * Create: Use an INSERT SQL statement.
  * Read: Use a SELECT SQL statement.
  * Update: Use an UPDATE SQL statement.
  * Delete: Use a DELETE SQL statement.
    Example:

  <pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">// Insert
  String insertSQL = "INSERT INTO users (name, email) VALUES (?, ?)";
  PreparedStatement pstmt = connection.prepareStatement(insertSQL);
  pstmt.setString(1, "John Doe");
  pstmt.setString(2, "john.doe@example.com");
  pstmt.executeUpdate();

  // Select
  String selectSQL = "SELECT * FROM users";
  ResultSet rs = stmt.executeQuery(selectSQL);
  while (rs.next()) {
      System.out.println(rs.getString("name") + " " + rs.getString("email"));
  }

  // Update
  String updateSQL = "UPDATE users SET email = ? WHERE name = ?";
  PreparedStatement pstmt2 = connection.prepareStatement(updateSQL);
  pstmt2.setString(1, "john.new@example.com");
  pstmt2.setString(2, "John Doe");
  pstmt2.executeUpdate();

  // Delete
  String deleteSQL = "DELETE FROM users WHERE name = ?";
  PreparedStatement pstmt3 = connection.prepareStatement(deleteSQL);
  pstmt3.setString(1, "John Doe");
  pstmt3.executeUpdate();
  </code></div></div></pre>

### # What is connection pooling and why is it important?

* Connection pooling is a technique used to manage database connections in a pool to be reused for future requests. This reduces the overhead of creating and closing connections frequently, leading to improved performance and resource utilization.

### # How do you handle transactions in JDBC?

* Transactions in JDBC can be managed using the `setAutoCommit`, `commit`, and `rollback` methods of the Connection object.
  Example:
  <pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">try {
      connection.setAutoCommit(false);

      // Perform SQL operations
      String updateSQL = "UPDATE accounts SET balance = balance - 100 WHERE id = ?";
      PreparedStatement pstmt = connection.prepareStatement(updateSQL);
      pstmt.setInt(1, 1);
      pstmt.executeUpdate();

      String updateSQL2 = "UPDATE accounts SET balance = balance + 100 WHERE id = ?";
      PreparedStatement pstmt2 = connection.prepareStatement(updateSQL2);
      pstmt2.setInt(1, 2);
      pstmt2.executeUpdate();

      connection.commit();
  } catch (SQLException e) {
      connection.rollback();
      e.printStackTrace();
  } finally {
      connection.setAutoCommit(true);
  }
  </code></div></div></pre>

### # What are some best practices for using JDBC?

* Some best practices for using JDBC include:
  * Always close resources (Connection, Statement, ResultSet) in a finally block or use try-with-resources.
  * Use PreparedStatement to prevent SQL injection.
  * Use connection pooling to manage database connections efficiently.
  * Handle exceptions properly and log them for debugging.

### # What is a PreparedStatement and how is it different from a Statement?

* A PreparedStatement is a precompiled SQL statement that can be executed multiple times with different parameters. It is more efficient and secure compared to a Statement, as it helps prevent SQL injection attacks.
  Example:
  <pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">String sql = "SELECT * FROM users WHERE email = ?";
  PreparedStatement pstmt = connection.prepareStatement(sql);
  pstmt.setString(1, "john.doe@example.com");
  ResultSet rs = pstmt.executeQuery();</code></div></div></pre>
