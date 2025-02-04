# Portfolio

Using HTML, CSS, JS

## Live 
 -> [Open Portfolio](https://gauravprakashh.netlify.app/)

## How to Fork this Repository

1. **Fork the Repository**:
   - Click on the 'Fork' button at the top right corner of this repository page.
   - This will create a copy of this repository in your GitHub account.

2. **Clone the Forked Repository**:
   - Open your terminal or command prompt.
   - Run the following command to clone the repository to your local machine:
     ```sh
     git clone https://github.com/YOUR_USERNAME/portfolio.git
     ```
   - Replace `YOUR_USERNAME` with your GitHub username.

3. **Navigate to the Project Directory**:
   - Change into the project directory:
     ```sh
     cd portfolio
     ```

4. **Open the Project**:
   - You can now open the project in your preferred code editor and start making changes.

## HTML Structure

The HTML file is structured as follows:

1. **Header Section**: Contains the navigation bar and a brief introduction.
   - Navigation bar with links to different sections of the page.
   - Introduction text with a title and a brief description.

2. **About Section**: Provides information about the individual.
   - Image and description.
   - Tabs for skills, experience, and education.

3. **Services Section**: Lists the services offered.
   - Each service is described with an icon, title, and description.

4. **Portfolio Section**: Showcases the work done.
   - Each work item includes an image, title, description, and a link to the GitHub repository.

5. **Contact Section**: Provides contact information and a form to send messages.
   - Contact details and social media links.
   - Contact form to submit messages.

6. **Footer Section**: Contains copyright information.

## JavaScript

- **Tab Functionality**: Allows switching between different tabs in the About section.
- **Menu Functionality**: Handles the opening and closing of the side menu on smaller screens.
- **Form Submission**: Submits the contact form to a Google Sheet and displays a success message.

## CSS

- **Styling**: Provides the overall look and feel of the website.
- **Responsive Design**: Ensures the website looks good on different screen sizes.

## Integrating Form with Google Sheets

To integrate the form with Google Sheets, follow these steps:

1. **Create a Google Sheet**:
   - Go to [Google Sheets](https://sheets.google.com) and create a new sheet.
   - Name the columns as per your form fields (e.g., Name, Email, Message).

2. **Deploy a Google Script**:
   - Open the Google Sheet and go to `Extensions` > `Apps Script`.
   - Delete any code in the script editor and paste the code from the [form-to-google-sheets repository](https://github.com/jamiewilson/form-to-google-sheets).
   - Save the script and click on the `Deploy` button.
   - Select `New deployment`, choose `Web app`, and set the access to `Anyone`.
   - Copy the Web App URL.

3. **Update the HTML Form**:
   - In your HTML file, update the form action URL to the Web App URL you copied.
   - Ensure the form fields' names match the column names in your Google Sheet.

4. **JavaScript for Form Submission**:
   - Add the JavaScript code to handle form submission and display a success message.

Example:
```html
<form name="submit-to-google-sheet">
  <input type="text" name="Name" placeholder="Your Name" required />
  <input type="email" name="Email" placeholder="Your Email" required />
  <textarea name="Message" rows="6" placeholder="Your Message"></textarea>
  <button type="submit" class="btn btn2">Submit</button>
</form>
<span id="msg">Click on SUBMIT to send me message</span>
```
```JS
<script>
  const scriptURL = 'YOUR_WEB_APP_URL';
  const form = document.forms['submit-to-google-sheet'];
  const msg = document.getElementById('msg');

  form.addEventListener('submit', (e) => {
    e.preventDefault();
    fetch(scriptURL, { method: 'POST', body: new FormData(form) })
      .then((response) => {
        msg.innerHTML = 'Message Sent Successfully';
        setTimeout(() => {
          msg.innerHTML = 'Click on SUBMIT to send me message';
        }, 5000);
        form.reset();
      })
      .catch((error) => console.error('Error!', error.message));
  });
</script>
```

❤️ Happy Coding ❤️

