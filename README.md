# CS50’s Web Programming with Python and JavaScript: Mail Project

## Overview

This project is part of Harvard's CS50 Web Programming with Python and JavaScript course. The goal of the project is to design a front-end for an email client that makes API calls to send and receive emails, implementing various features like composing emails, viewing inbox, and managing email states such as read/unread or archived/unarchived.

## Getting Started

1. **Download the distribution code**:  
   Download the project code from [here](https://cdn.cs50.net/web/2020/spring/projects/3/mail.zip) and unzip it.

2. **Setup the Django environment**:
    - Open your terminal and navigate to the `mail` directory where the project was extracted.
    - Run the following commands to set up the database:
        ```bash
        python manage.py makemigrations mail
        python manage.py migrate
        ```

3. **Start the server**:
    - Run the server by executing:
        ```bash
        python manage.py runserver
        ```
    - Open the web browser and go to `http://localhost:8000/`.

4. **Create an Account**:
    - Use the "Register" link to create a new user account. The emails will be stored in the database and won't be sent to real servers.

5. **Usage**:
    - Upon successful login, the user will be redirected to the Inbox page, which will initially be empty.
    - Navigate between your Sent, Inbox, and Archived mailboxes using the navigation buttons.
    - The "Compose" button lets users create a new email.

## Application Flow

- **Inbox**: Displays all received emails in reverse chronological order.
- **Compose**: A form where you can write and send a new email. After sending, the email is stored in the "Sent" mailbox.
- **View Email**: Clicking on an email will display its details (sender, subject, timestamp, and body).
- **Archive/Unarchive**: You can archive/unarchive emails when viewing them.
- **Reply**: You can reply to an email, with the recipient and subject pre-filled.

## JavaScript and API

This project involves implementing frontend functionality using JavaScript to interact with Django backend API. Here are the core API routes:

### API Endpoints

1. **GET /emails/<str:mailbox>**  
   Fetches emails from a given mailbox (Inbox, Sent, Archive).
   
2. **GET /emails/<int:email_id>**  
   Fetches a specific email by its ID.

3. **POST /emails**  
   Sends an email by providing recipients, subject, and body in the request body.

4. **PUT /emails/<int:email_id>**  
   Updates the email's status (e.g., read/unread, archived/unarchived).

### JavaScript Functions

- `compose_email()`: Toggles between the inbox and compose views, clears the form each time it's accessed.
- `load_mailbox(mailbox)`: Loads emails for a given mailbox (Inbox, Sent, or Archive).
- `view_email(email_id)`: Displays detailed content for a clicked email.
- `archive_email(email_id, archived)`: Archives or unarchives an email when the appropriate button is clicked.

## Implementation

The implementation involves writing JavaScript functions inside `inbox.js` to handle:

- **Email Composition**: Submit the composition form using a POST request to send an email.
- **Mailbox Navigation**: When visiting a mailbox, display the list of emails. Handle unread emails with specific visual styles.
- **Email Viewing**: Display the content of an email when clicked, and update the status as read.
- **Email Archiving**: Allow users to archive and unarchive emails.
- **Email Replying**: Pre-fill the composition form for replies.

### Example JavaScript for Fetching Emails
```javascript
fetch('/emails/inbox')
  .then(response => response.json())
  .then(emails => {
    // Process and display emails in the inbox
    console.log(emails);
  });
```

### Example JavaScript for Sending an Email
```javascript
fetch('/emails', {
  method: 'POST',
  body: JSON.stringify({
    recipients: 'baz@example.com',
    subject: 'Meeting time',
    body: 'How about we meet tomorrow at 3pm?'
  })
})
.then(response => response.json())
.then(result => {
  // Handle successful sending of email
  console.log(result);
});
```

## Requirements

- **Frontend**: HTML, CSS, and JavaScript (to handle the user interface).
- **Backend**: Django (pre-configured in the distribution code).
- **API calls**: JavaScript `fetch()` to interact with the backend APIs.

## Design and Interaction

### Views:

- **Inbox Page**: Displays a list of received emails.
- **Compose View**: Form to create and send an email.
- **Email View**: View the full content of an email.
- **Archive/Unarchive**: Users can archive/unarchive emails they received.

### Styling:
You can edit `styles.css` to customize the look and feel of the mail client.

## How to Submit

1. Push the changes to your GitHub repository.
2. Submit your project via the CS50 submission system on GitHub.
3. Ensure the folder structure matches the one provided, with no extra folders or files.

## Conclusion

This project demonstrates how to create a full-featured web application using Django for the backend and JavaScript for the frontend. It involves using APIs for email operations like reading, sending, and managing emails, while also ensuring an interactive user experience.
https://youtu.be/-G9c2P6zpDQ?si=-9TbeRWqFWm49hN5
