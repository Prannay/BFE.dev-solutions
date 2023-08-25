import React, { useState, useEffect } from "react";
import "./styles.css";

export default function App() {
  const [inpval, setInpval] = useState("");

  const handleChange = (event) => {
    let val = event.target.value;
    if (
      (val.includes("(") && !val.includes(")")) ||
      (val.includes(")") && !val.includes("("))
    ) {
      val = val.replace(/[()-]/g, "");
      setInpval(val);
      return;
    }
    val = val.replace(/[()-]/g, "");
    if (isNaN(Number(val))) {
      return;
    }
    if (val.length > 10) {
      return;
    }
    if (val.length >= 3) {
      let v = "(" + val.substring(0, 3) + ")" + val.substring(3);
      setInpval(v);
      if (v.length > 8) {
        setInpval(v.substring(0, 8) + "-" + v.substring(8));
      }
    } else {
      setInpval(val);
    }
  };

  return (
    <div className="App">
      <input onChange={handleChange} type="text" value={inpval} />
    </div>
  );
}
