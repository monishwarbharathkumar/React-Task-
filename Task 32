import React, {useCallback, useEffect, useMemo, useState} from "react";

const API = "https://jsonplaceholder.typicode.com/users";

function App() {
  const [users, setUsers] = useState([]);
  const [filter, setFilter] = useState("");
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  useEffect(() => {
    const controller = new AbortController();

    async function fetchUsers() {
      setLoading(true);
      setError("");

      try {
        const response = await fetch(
          `${API}?name_like=${encodeURIComponent(filter)}`,
          { signal: controller.signal }
        );

        if (!response.ok) {
          throw new Error("Failed to fetch users");
        }

        const data = await response.json();
        setUsers(data);
      } catch (err) {
        if (err.name !== "AbortError") {
          setError(err.message);
        }
      } finally {
        setLoading(false);
      }
    }

    fetchUsers();

    return () => {
      controller.abort();
      console.log("Cleanup: previous fetch aborted");
    };
  }, [filter]);

  const refreshUsers = useCallback(async () => {
    const response = await fetch(
      `${API}?name_like=${encodeURIComponent(filter)}`
    );
    const data = await response.json();
    setUsers(data);
  }, [filter]);

  const averageId = useMemo(() => {
    console.log("Calculating average...");

    if (!users.length) return 0;

    return (
      users.reduce((total, user) => total + user.id, 0) /
      users.length
    ).toFixed(2);
  }, [users]);

  return (
    <div style={{ padding: 30, fontFamily: "Arial" }}>
      <h1>Users</h1>

      <input
        value={filter}
        onChange={(e) => setFilter(e.target.value)}
        placeholder="Filter by name..."
      />

      <button onClick={refreshUsers} style={{ marginLeft: 10 }}>
        Refresh
      </button>

      {loading && <p>Loading...</p>}
      {error && <p style={{ color: "red" }}>{error}</p>}

      <h3>Average User ID: {averageId}</h3>

      {users.length === 0 && !loading ? (
        <p>No users found.</p>
      ) : (
        <ul>
          {users.map((user) => (
            <li key={user.id}>
              <strong>{user.name}</strong> — {user.email}
            </li>
          ))}
        </ul>
      )}
    </div>
  );
}

export default App;
