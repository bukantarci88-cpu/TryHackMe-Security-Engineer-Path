# Eng 4.8. Mothers Secret

**Mother's Secret: Exploit flaws found in Mother's code to reveal its secrets.**

In this challenge, you will investigate the TryHackMe Cargo Star Ship (THMCSS) Nostromo, owned by the Weyland-TryHackMe Corps and its compromised computer system, MU-TH-UR 6000. Your mission is to uncover hidden secrets by exploiting vulnerabilities in the web application running on the Nostromo server. Get ready to put your code analysis and exploitation skills to the test!

Setting Up: 

1. Start the AttackBox.
2. Start the Lab Machine provided for this challenge and note the Machine's IP address; you will need it later to access the web app.
3. You can now open the AttackBox and enter the MU-TH-UR 6000 server's IP address in the browser running on port 80.

Upon accessing the MU-TH-UR6000 computer, AKA Mother, you will see the Mother UI server. However, since you only have a "Crew" Member level role, you only have read access to limited resources. But there are other ways to access it. Can you find them and uncover Mother's secret?

**Equipment Check:** Download the files attached to this task to review the code.

1. Explore the available endpoints of the Mother Server and try to find any clues that can reveal mother's secret.
2. Search for a file that contains essential information about the ship's activities.
3. Exploit the vulnerable code to download the secrets from the server. Can you spot the vulnerable code?
4. Capture all the hidden flags you encounter during your exploration. Only Mother holds this secret.

**Operating Manual:** Below are some sequences and operations to get you started. Use the following to unlock information and navigate Mother:

- Emergency command override is 100375. Use it when accessing *Alien Loaders*.
- Download the task files to learn about Mother's routes.
- Hitting the *routes* in the *right* order makes Mother confused, it might think you are a Science Officer!

I used **yaml.js** and **nostromo.js** from the GitHub repository *Scientistz/mothersSecret*.

The process starts with **YAML**, followed by **nostromo.js**, which sends a POST request. After accessing the `/nostromo` endpoint and setting `isNostromoAuthenticate = true`, the user is authenticated. If the authentication check passes, the application returns the answers.

```jsx
fs.readFile(filePath, "utf8", (err, data) => {
if (err) {
res.status(500).json({
status: "error",
message: "Science Officer Eyes Only",
});
return;
}
```

The application contains three endpoints:

- `/yaml`
- `/nostromo`
- `/nostromo/mother`

The analysis began by examining the `/yaml` endpoint. After reviewing the code, I used **yaml.js** and **nostromo.js** from the GitHub repository *Scientistz/mothersSecret* to understand how the application processes requests.

The `/nostromo` endpoint handles POST requests. During the code review, I identified the `isNostromoAuthenticate` variable. When this value is set to `true`, the user is successfully authenticated. After authentication succeeds, access to the `/nostromo/mother` endpoint reveals the answers.

<img width="451" height="162" alt="image" src="https://github.com/user-attachments/assets/e2338c67-0ad6-49ab-9b1d-f4da07cbc45d" />


From source 

<img width="1033" height="473" alt="image 1" src="https://github.com/user-attachments/assets/35268caa-33fe-48a9-8b42-516d22ba8136" />


I investigated the page source, followed the URL referenced in the source code, and analyzed the JavaScript files. Using **jsbeautifier.org** to deobfuscate and format the code, I was able to identify the application's endpoints and understand the authentication logic.

<img width="1898" height="487" alt="image 2" src="https://github.com/user-attachments/assets/9c426fd9-c2b6-4630-b0a5-a82cbed2dcdc" />


**Can you guess what is /api/nostromo/mother/secret.txt?**

<img width="1433" height="673" alt="image 3" src="https://github.com/user-attachments/assets/f2db7098-8842-4dbf-8b93-fae640abb486" />


**Answer the questions below**

> What is the number of the emergency command override?
> 

100375

<img width="588" height="222" alt="image 4" src="https://github.com/user-attachments/assets/ebb294cf-7013-4eb0-9c1f-00314995cea0" />


> What is the special order number?
> 

937 

After investigating the page source and reviewing the Network tab, I identified a POST request being sent to the `/api/nostromo` endpoint.

To replicate the request, I configured the following:

- Method: `POST`
- Endpoint: `/api/nostromo`
- Header: `Content-Type: application/json`

Next, I obtained the value `0RD3R_937.txt` from the `.yaml` file and included it in the JSON request body. After sending the POST request with the required payload and headers, the application processed the request and returned the expected response.

<img width="1435" height="713" alt="image 5" src="https://github.com/user-attachments/assets/d4f12ea4-0c17-4a5f-bb6f-ddadc8bdebc4" />


> What is the hidden flag in the Nostromo route?
> 

Flag{X3n0M0Rph}

<img width="561" height="240" alt="image 6" src="https://github.com/user-attachments/assets/7ae72c2d-8e00-4fe9-8447-216bc85f276b" />


> What is the name of the Science Officer with permissions?
> 

Ash

<img width="533" height="647" alt="image 7" src="https://github.com/user-attachments/assets/c955774b-3bcd-4849-8053-ad7b22b7565d" />


> What are the contents of the classified "Flag" box?
> 

THM_FLAG{0RD3R_937}

<img width="628" height="661" alt="image 8" src="https://github.com/user-attachments/assets/210b1627-10a4-4121-aa2f-08553dbfa64f" />


> Where is Mother's secret?
> 

*/opt/m0th3r*

<img width="1431" height="700" alt="image 9" src="https://github.com/user-attachments/assets/d36345e7-4b00-42af-936b-f34690bc47a8" />


> What is Mother's secret?
> 

Flag{Ensure_return_of_organism_meow_meow!}

<img width="1433" height="456" alt="image 10" src="https://github.com/user-attachments/assets/ba2606ef-c0eb-46c3-a6de-bcaaeadc6149" />
