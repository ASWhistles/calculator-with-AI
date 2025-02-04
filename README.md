# calculator-with-AI
This week's assignment was to use AI to create a calculator!
My prompt was "Please, make a modern calculator with pink, rounded buttons".
Here is the result:

![calculator image](https://github.com/user-attachments/assets/434ae530-d3ea-40df-8067-5fc19495b551)



https://github.com/user-attachments/assets/70298e35-3e34-4bd5-9b57-1ca99ccde315

Here is the code:

import { useState } from "react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";

export default function Calculator() {
  const [input, setInput] = useState("");

  const handleClick = (value) => {
    if (value === "=") {
      try {
        setInput(eval(input).toString());
      } catch {
        setInput("Error");
      }
    } else if (value === "C") {
      setInput("");
    } else {
      setInput(input + value);
    }
  };

  return (
    <div className="flex justify-center items-center min-h-screen bg-gradient-to-br from-pink-300 to-blue-300">
      <Card className="p-4 bg-white shadow-lg rounded-2xl w-72">
        <CardContent className="text-center">
          <div className="text-2xl bg-gray-200 p-3 rounded-md mb-3">{input || "0"}</div>
          <div className="grid grid-cols-4 gap-2">
            {["7", "8", "9", "/", "4", "5", "6", "*", "1", "2", "3", "-", "C", "0", "=", "+"].map((item) => (
              <Button
                key={item}
                className="text-xl p-4 rounded-lg bg-pink-400 text-white hover:bg-pink-500"
                onClick={() => handleClick(item)}
              >
                {item}
              </Button>
            ))}
          </div>
        </CardContent>
      </Card>
    </div>
  );
}
