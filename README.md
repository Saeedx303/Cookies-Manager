# How to Add the Cookie Consent Popup to Your Blogger Website

Follow these steps to add the cookie consent popup to your Blogger site:

## Step 1: Access Your Blogger Dashboard
1. Log in to your Blogger account
2. Select the blog you want to add the cookie consent popup to

## Step 2: Add the Code to Your Blog
1. In your Blogger dashboard, go to "Theme" (or "Layout" in older versions)
2. Click on "Edit HTML" (or "Edit Theme HTML" in older versions)
3. Find the `</body>` tag in your theme HTML (it should be near the end of the file)
4. Paste the following code just before the `</body>` tag:

```html
<!-- Cookie Consent Popup -->
<style>
  .cookie-popup {
    width: 300px;
    height: 220px;
    background-color: rgb(255, 255, 255);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 20px 30px;
    gap: 13px;
    position: fixed;
    bottom: 20px;
    right: 20px;
    overflow: hidden;
    box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.062);
    border-radius: 8px;
    z-index: 9999;
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.3s ease, transform 0.3s ease;
  }

  .cookie-popup.show {
    opacity: 1;
    transform: translateY(0);
  }

  .cookie-popup.hide {
    opacity: 0;
    transform: translateY(20px);
    pointer-events: none;
  }

  #cookieSvg {
    width: 50px;
  }

  #cookieSvg g path {
    fill: rgb(97, 81, 81);
  }

  .cookieHeading {
    font-size: 1.2em;
    font-weight: 800;
    color: rgb(26, 26, 26);
    margin: 0;
  }

  .cookieDescription {
    text-align: center;
    font-size: 0.7em;
    font-weight: 600;
    color: rgb(99, 99, 99);
    margin: 0;
  }

  .buttonContainer {
    display: flex;
    gap: 20px;
    flex-direction: row;
  }

  .acceptButton {
    width: 80px;
    height: 30px;
    background-color: #7b57ff;
    transition-duration: .2s;
    border: none;
    color: rgb(241, 241, 241);
    cursor: pointer;
    font-weight: 600;
    border-radius: 20px;
  }

  .declineButton {
    width: 80px;
    height: 30px;
    background-color: rgb(218, 218, 218);
    transition-duration: .2s;
    color: rgb(46, 46, 46);
    border: none;
    cursor: pointer;
    font-weight: 600;
    border-radius: 20px;
  }

  .declineButton:hover {
    background-color: #ebebeb;
    transition-duration: .2s;
  }

  .acceptButton:hover {
    background-color: #9173ff;
    transition-duration: .2s;
  }
</style>

<div class="cookie-popup" id="cookiePopup">
  <svg version="1.1" id="cookieSvg" x="0px" y="0px" viewBox="0 0 122.88 122.25" xml:space="preserve">
    <g>
      <path d="M101.77,49.38c2.09,3.1,4.37,5.11,6.86,5.78c2.45,0.66,5.32,0.06,8.7-2.01c1.36-0.84,3.14-0.41,3.97,0.95 c0.28,0.46,0.42,0.96,0.43,1.47c0.13,1.4,0.21,2.82,0.24,4.26c0.03,1.46,0.02,2.91-0.05,4.35h0v0c0,0.13-0.01,0.26-0.03,0.38 c-0.91,16.72-8.47,31.51-20,41.93c-11.55,10.44-27.06,16.49-43.82,15.69v0.01h0c-0.13,0-0.26-0.01-0.38-0.03 c-16.72-0.91-31.51-8.47-41.93-20C5.31,90.61-0.73,75.1,0.07,58.34H0.07v0c0-0.13,0.01-0.26,0.03-0.38 C1,41.22,8.81,26.35,20.57,15.87C32.34,5.37,48.09-0.73,64.85,0.07V0.07h0c1.6,0,2.89,1.29,2.89,2.89c0,0.4-0.08,0.78-0.23,1.12 c-1.17,3.81-1.25,7.34-0.27,10.14c0.89,2.54,2.7,4.51,5.41,5.52c1.44,0.54,2.2,2.1,1.74,3.55l0.01,0 c-1.83,5.89-1.87,11.08-0.52,15.26c0.82,2.53,2.14,4.69,3.88,6.4c1.74,1.72,3.9,3,6.39,3.78c4.04,1.26,8.94,1.18,14.31-0.55 C99.73,47.78,101.08,48.3,101.77,49.38L101.77,49.38z M59.28,57.86c2.77,0,5.01,2.24,5.01,5.01c0,2.77-2.24,5.01-5.01,5.01 c-2.77,0-5.01-2.24-5.01-5.01C54.27,60.1,56.52,57.86,59.28,57.86L59.28,57.86z M37.56,78.49c3.37,0,6.11,2.73,6.11,6.11 s-2.73,6.11-6.11,6.11s-6.11-2.73-6.11-6.11S34.18,78.49,37.56,78.49L37.56,78.49z M50.72,31.75c2.65,0,4.79,2.14,4.79,4.79 c0,2.65-2.14,4.79-4.79,4.79c-2.65,0-4.79-2.14-4.79-4.79C45.93,33.89,48.08,31.75,50.72,31.75L50.72,31.75z M119.3,32.4 c1.98,0,3.58,1.6,3.58,3.58c0,1.98-1.6,3.58-3.58,3.58s-3.58-1.6-3.58-3.58C115.71,34.01,117.32,32.4,119.3,32.4L119.3,32.4z M93.62,22.91c2.98,0,5.39,2.41,5.39,5.39c0,2.98-2.41,5.39-5.39,5.39c-2.98,0-5.39-2.41-5.39-5.39 C88.23,25.33,90.64,22.91,93.62,22.91L93.62,22.91z M97.79,0.59c3.19,0,5.78,2.59,5.78,5.78c0,3.19-2.59,5.78-5.78,5.78 c-3.19,0-5.78-2.59-5.78-5.78C92.02,3.17,94.6,0.59,97.79,0.59L97.79,0.59z M76.73,80.63c4.43,0,8.03,3.59,8.03,8.03 c0,4.43-3.59,8.03-8.03,8.03s-8.03-3.59-8.03-8.03C68.7,84.22,72.29,80.63,76.73,80.63L76.73,80.63z M31.91,46.78 c4.8,0,8.69,3.89,8.69,8.69c0,4.8-3.89,8.69-8.69,8.69s-8.69-3.89-8.69-8.69C23.22,50.68,27.11,46.78,31.91,46.78L31.91,46.78z M107.13,60.74c-3.39-0.91-6.35-3.14-8.95-6.48c-5.78,1.52-11.16,1.41-15.76-0.02c-3.37-1.05-6.32-2.81-8.71-5.18 c-2.39-2.37-4.21-5.32-5.32-8.75c-1.51-4.66-1.69-10.2-0.18-16.32c-3.1-1.8-5.25-4.53-6.42-7.88c-1.06-3.05-1.28-6.59-0.61-10.35 C47.27,5.95,34.3,11.36,24.41,20.18C13.74,29.69,6.66,43.15,5.84,58.29l0,0.05v0h0l-0.01,0.13v0C5.07,73.72,10.55,87.82,20.02,98.3 c9.44,10.44,22.84,17.29,38,18.1l0.05,0h0v0l0.13,0.01h0c15.24,0.77,29.35-4.71,39.83-14.19c10.44-9.44,17.29-22.84,18.1-38l0-0.05 v0h0l0.01-0.13v0c0.07-1.34,0.09-2.64,0.06-3.91C112.98,61.34,109.96,61.51,107.13,60.74L107.13,60.74z M116.15,64.04L116.15,64.04 L116.15,64.04L116.15,64.04z M58.21,116.42L58.21,116.42L58.21,116.42L58.21,116.42z"></path>
    </g>
  </svg>
  <p class="cookieHeading">We use cookies.</p>
  <p class="cookieDescription">This website uses cookies to ensure you get the best experience on our site.</p>

  <div class="buttonContainer">
    <button class="acceptButton" id="acceptCookies">Allow</button>
    <button class="declineButton" id="declineCookies">Decline</button>
  </div>
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    // Check if user has already made a choice
    const cookieConsent = localStorage.getItem('cookieConsent');
    const cookiePopup = document.getElementById('cookiePopup');
    
    // If no choice has been made yet, show the popup
    if (cookieConsent === null) {
      setTimeout(function() {
        cookiePopup.classList.add('show');
      }, 1000);
    }
    
    // Handle accept button click
    document.getElementById('acceptCookies').addEventListener('click', function() {
      localStorage.setItem('cookieConsent', 'accepted');
      cookiePopup.classList.remove('show');
      cookiePopup.classList.add('hide');
    });
    
    // Handle decline button click
    document.getElementById('declineCookies').addEventListener('click', function() {
      localStorage.setItem('cookieConsent', 'declined');
      cookiePopup.classList.remove('show');
      cookiePopup.classList.add('hide');
    });
  });
</script>
<!-- End Cookie Consent Popup -->
```

5. Click "Save" to apply the changes to your blog

## Step 3: Verify the Cookie Consent Popup
1. Visit your blog in a new browser window or in incognito mode
2. The cookie consent popup should appear at the bottom right of your screen after about 1 second
3. Test both the "Allow" and "Decline" buttons to make sure they work correctly

## Customization Options

### Change the Colors
To change the color of the "Allow" button, find this line in the CSS:
```css
.acceptButton {
  background-color: #7b57ff; /* Change this color */
}
```

To change the color when hovering over the "Allow" button:
```css
.acceptButton:hover {
  background-color: #9173ff; /* Change this color */
}
```

### Change the Text
To change the heading text, find this line:
```html
<p class="cookieHeading">We use cookies.</p>
```

To change the description text, find this line:
```html
<p class="cookieDescription">This website uses cookies to ensure you get the best experience on our site.</p>
```

### Change the Position
To change the position of the popup, find these lines in the CSS:
```css
.cookie-popup {
  /* ... other styles ... */
  bottom: 20px; /* Change to 'top: 20px' to move to top */
  right: 20px; /* Change to 'left: 20px' to move to left */
  /* ... other styles ... */
}
```

## How It Works
- The popup uses localStorage to remember the user's choice
- Once a user clicks either "Allow" or "Decline", the popup won't show again
- The popup is styled with CSS and animated with transitions
- The cookie icon is an SVG that's included directly in the HTML
