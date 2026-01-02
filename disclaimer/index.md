---
layout: disclaimer
title: Disclaimer
permalink: /disclaimer/
robots: noindex, nofollow
---

<div class="disclaimer-card">
  <h1>Disclaimer</h1>
  <p>The information provided on this site is for general informational purposes only and is not intended as professional advice. Use the content at your own risk; the site owner makes no guarantees about completeness, accuracy, or reliability. By continuing, you accept that the site owner is not liable for any losses or damages arising from your use of this site.</p>
  <button id="acceptDisclaimer" type="button">I understand — continue</button>
</div>

<script>
  (function () {
    var button = document.getElementById('acceptDisclaimer');
    if (!button) return;

    button.addEventListener('click', function () {
      try {
        localStorage.setItem('disclaimerAccepted:v1', 'true');
      } catch (e) {
        /* localStorage may be unavailable; continue without blocking */
      }

      var redirect = null;
      try {
        redirect = sessionStorage.getItem('postDisclaimerRedirect');
      } catch (e) {
        /* sessionStorage may be unavailable; default redirect will be used */
      }

      if (redirect) {
        window.location.href = redirect;
      } else {
        window.location.href = "{{ '/' | relative_url }}";
      }
    });
  })();
</script>
