TUITIONAPP PWA files

Upload these files/folders to the ROOT of your GitHub repository:
- manifest.json
- sw.js
- icons/ (folder containing icon-192.png and icon-512.png)

Then edit index.html:

1) Find the line:
</head>

Add this immediately BEFORE it:
<link rel="manifest" href="/TUITIONAPP/manifest.json">
<meta name="theme-color" content="#171d35">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">

2) Find the final line:
</body></html>

Add this immediately BEFORE </body>:
<script>
if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker.register("/TUITIONAPP/sw.js")
      .catch((error) => console.log("Service worker registration failed:", error));
  });
}
</script>

Save/commit the change. Wait for GitHub Pages to redeploy.

Then open https://raj2006rk2006-bot.github.io/TUITIONAPP/ in Chrome (not inside another app), refresh once, tap Chrome menu ⋮, and choose Install app if shown.

Note: this makes the current demo installable and gives basic offline caching. It does NOT add cloud sync, parent login, or automatic WhatsApp reminders. Current student data remains in the browser on that device.
