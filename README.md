# Api

import "./styles.css";
import { useEffect, useState } from "react";
import axios from "axios";

const ERR = "Something is wrong 404";
export default function App() {
  const [data, setData] = useState([]);
  const [isError, serError] = useState(false);
  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/post")
      .then((res) => setData(res.data))
      .catch((err) => serError(err.message));
  }, []);

  return (
    <div className="App">
      <h2> AXIOS TUTORIALS </h2>
      {isError ? ERR : null}
      {data.map((post) => {
        const { id, title, body } = post;
        return (
          <div key={id}>
            <h2>{id}</h2>
            <h2>{title}</h2>
            <h2>{body}</h2>
          </div>
        );
      })}
      <h1>Hello CodeSandbox</h1>
      <h2>Start editing to see some magic happen!</h2>
    </div>
  );
}
