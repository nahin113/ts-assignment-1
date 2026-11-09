Using typeof
The typeof operator is used to check primitive types like strings, numbers, or booleans at runtime. In the function below, it helps TypeScript determine whether the input should be handled as a string or a number.

TypeScript
function formatValue(input: string | number): string {
  if (typeof input === "string") {
    return input.toUpperCase();
  } else {
    return input.toFixed(2);
  }
}
Using instanceof
The instanceof operator checks if an object is an instance of a specific class or constructor function. It is commonly used in error handling to verify that a caught exception is an instance of the Error class before accessing its properties.

TypeScript
try {
  throw new Error("Failed to connect to the database!");
} catch (error: unknown) {
  if (error instanceof Error) {
    console.log("Error message:", error.message);
  } else {
    console.log("An unknown error occurred:", error);
  }
}
Using the in operator
The in operator checks if a specific property exists within an object, making it ideal for narrowing down union types of different interfaces. In the example below, it distinguishes between an Admin and a Guest based on their unique properties.

TypeScript
interface Admin {
  name: string;
  adminLevel: number;
}

interface Guest {
  name: string;
  guestPassId: string;
}

function handleUserAccess(user: Admin | Guest): void {
  if ("adminLevel" in user) {
    console.log(`Welcome Admin ${user.name}. Level: ${user.adminLevel}`);
  } else {
    console.log(`Welcome Guest ${user.name}. Pass ID: ${user.guestPassId}`);
  }
}
Conclusion
Type narrowing ensures strict type safety and eliminates unhandled runtime bugs in dynamic applications. Utilizing these guard operators allows TypeScript to accurately infer data types and provide intelligent auto-completion throughout your codebase.
