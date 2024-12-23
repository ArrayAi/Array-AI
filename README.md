# Arrays-AI

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[![TypeScript](https://img.shields.io/badge/TypeScript-Ready-blue.svg)](https://www.typescriptlang.org/)

[![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow.svg)](https://www.javascript.com/)

The Arrays AI library enriches JavaScript arrays with artificial intelligence capabilities, empowering data analysis tasks. It seamlessly integrates with JavaScript, specifically designed to complement its functionality and not to replace it. This library is particularly useful for performing advanced data analysis operations on arrays of objects. It leverages the power of artificial intelligence and the OpenAI API to process natural language commands, enabling efficient filtering, aggregation, sorting, and removal of elements within the array. By combining the flexibility of JavaScript with the intelligence of the Arrays AI library, developers can achieve sophisticated data analysis and manipulation workflows.

## **Installation**

To install the library, you can use NPM:

```bash
npm install arrays-ai
```

You can also download the source code from the GitHub repository and use it directly in your project.

## **Usage**

To use the library in your project, you must first import it:

```typescript
import * as dotenv from "dotenv";
dotenv.config({ path: './.env' });
import { ArraysAi, Languages, Configuration } from '../dist/index';

// Get the OPEN AI API KEY from the .env file
dotenv.config();
let APIKEY = process.env.OPENAI_API_KEY;
if(APIKEY == undefined) throw new Error("APIKEY not found in .env file");

// Configure with the OPEN AI API KEY
let config : Configuration = new Configuration({
  apiKey: APIKEY
});

// configure the arraysai object
const arraysai : ArraysAi<any> = new ArraysAi();
arraysai.Configure(config);

// Set the arrays to be used in the questions
let arrays = [collection_1, collection_2, ...];
arraysai.SetData(arrays);

// Language used in the verbose answers by default use English
arraysai.SetLanguage(Languages.ENGLISH);

```

After that, you can manipulate an array of objects using the "Ask()" function. This function takes as parameters the array to manipulate and a query string that indicates the operation to perform and a boolean value in case you whant a verbose response. For example:

```typescript
arraysai.Ask("How many records have a null age in the first array???", true)
.then(answer => 
  {
      console.log(answer); // There are two records in the first array that have a null age.
    }
  );
```

The "Ask()" function uses OpenAI's artificial intelligence to interpret the query and perform the corresponding manipulation on the array. The result is returned through a string for verbose answers or any for simple questions.


## **TypeScript Support**


The "arrays-ai" library is fully compatible with TypeScript. Starting from version 1.1.1, the library includes TypeScript declaration files (.d.ts) that allow for type checking at compile time and better editor support.

To use the library in your TypeScript project, simply install the package via NPM:

```bash
npm install arrays-ai
```

## **Documentation**

The "arrays-ai" library has the following API:

| Method | Description |
| --- | --- |
| Configure(OpenAiConfig: Configuration, OutputLanguage?: BuilInLanguage): void | Configures the OpenAI API and the output language (optional). |
| SetLanguage(Language: Languages): void | Sets the language used in the generated responses. |
| SetData(Data: Array<Array<T>>): void | Sets the data for the table. |
| GetData(): Array<Array<T>> | Gets the data from the table. |
| GetColumns(): Array<IColumns> | Gets the column information of the table. |
| SetTokenNumber(Tokens: number): void | Sets the maximum number of tokens for response generation. |
| SetTemperature(Temperature: number): void | Sets the temperature for response generation. |

The **`Ask(Question?: string, Verbose?: boolean): Promise<string | any>`** method is used to ask a question about the table data and retrieve the generated response from the OpenAI API.

- **`Question`** (optional): A string representing the question you want to ask about the table data.
- **`Verbose`** (optional): A boolean value indicating whether you want a detailed response or not. If set to **`true`**, the method will return a verbose response.

The method sends the provided question as a prompt to the OpenAI API, which generates a response based on the configured model and parameters. The generated response contains the answer or result based on the question asked.

If the **`Verbose`** parameter is set to **`true`**, the method will also generate a verbose response that includes the original question and the answer for better understanding.

The method returns a Promise that resolves to either a string or any data type depending on the response received from the API. The return value contains the generated response or the result of the question asked.

Please note that you need to configure the OpenAI API and set the table data using the **`Configure`** and **`SetData`** methods before calling the **`Ask`** method.

## **Enumeration: `Languages`**

| Value | Description |
| --- | --- |
| ENGLISH | Represents the English language. |
| SPANISH | Represents the Spanish language. |

## **Contributing**

If you want to contribute to the project, you can do the following:

- Report bugs or suggest improvements using the GitHub issues system.
- Propose new features or improve documentation using pull requests.

  
  
