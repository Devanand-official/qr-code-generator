# QR Generator (Node.js CLI)

A simple Node.js command-line QR generator that takes a URL from the user and produces a qr_image.png file.
Built using:

Inquirer – for terminal prompts

qr-image – to generate QR codes

fs – to save the output file

📦 Installation
1. Clone the repository
git clone <your-repo-url>
cd <your-project-folder>

2. Install dependencies
npm install

▶️ Usage

Run the script:

node index.js


You will see:

Type in your URL :


After entering your URL, a QR code image will be generated and saved as:

qr_image.png

📁 Code (index.js)
import inquirer from "inquirer";
import qr from "qr-image";
import fs from "fs";

inquirer
  .prompt([
    { message: "Type in your URL :", name: "URL" },
  ])
  .then((answers) => {
    const url = answers.URL;

    // Generate QR code PNG
    const qr_png = qr.image(url, { type: "png" });

    // Save file locally
    qr_png.pipe(fs.createWriteStream("qr_image.png"));
  })
  .catch((error) => {
    if (error.isTtyError) {
      console.log("Prompt could not be rendered in this environment.");
    } else {
      console.log("Something went wrong:", error);
    }
  });

📌 Output File

Generated file: qr_image.png

Location: Project root folder

Format: PNG QR Code

🧩 Requirements

Node.js (v16 or later recommended)

npm (comes with Node)

❗ Troubleshooting
Problem	Reason	Fix
Cannot find module 'inquirer'	Dependencies missing	Run npm install
QR file not created	Permission issue or wrong folder	Use a writable folder
Inquirer prompt not showing	Unsupported terminal	Use PowerShell / CMD / Bash
