DHL Leave Management Automation (Web + UiPath)
This project was developed for the DHL RPA Challenge and consists of two main components:
- A web-based leave management system (Node.js + MongoDB)
- A UiPath automation script that reads Excel data and fills the leave form automatically

📁 Project Structure
/web-solution     --> Node.js backend + HTML/CSS/JS frontend
/uipath-project   --> UiPath Studio folder (Main.xaml only)

🌐 Web Solution
Features:
- HR login authentication
- Submit and manage leave requests
- Approve or reject applications
- Prevents duplicate submissions
- Displays success/error messages using toast notifications

How to Run:
1. Open the `web-solution` folder in terminal
2. Run `npm install` to install dependencies
3. Create a `.env` file with the following contents:
PORT=3001
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
4. Run the server using `npm start`
5. Open http://localhost:3001/dashboard in browser

Default HR login:
- Username: admin
- Password: admin123

> The database will auto-create the first admin user using the seed script.

🤖 UiPath Automation (Main.xaml)
Features:
- Reads leave application data from Excel
- Logs in to the web portal
- Submits each row as a leave application
- If a duplicate is detected, it takes a screenshot
- Sends an email with error details and a screenshot attached

How to Run:
1. Open `Main.xaml` in UiPath Studio
2. Place your Excel file in a known folder and update the `Read Range` path
3. Set up the correct file path in the `Take Screenshot` and `Save Image` activities
4. Configure Outlook account in UiPath to enable `Send Outlook Mail Message`
5. Run the automation
6. At the end:
   - Successful entries will be submitted to the web app
   - Duplicate errors will trigger a screenshot + email to  smtuhin957@gmail.com

📧 Email Report
- If a duplicate or other error is found, a screenshot is taken
- An email is sent to: smtuhin957@gmail.com
- Email subject: Leave Update Error
- The email contains:
  - Total success count
  - Total failure count
  - Attached screenshots (if any)

