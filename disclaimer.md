---
layout: disclaimer
title: Disclaimer
permalink: /disclaimer/
robots: noindex, nofollow
---

<div class="disclaimer-modal" role="region" aria-label="Disclaimer">
  <div class="disclaimer-modal__card">
    <h1 class="disclaimer-modal__title">Before we continue</h1>

    <p class="disclaimer-modal__text">
      Quick legal thing. I'm sharing thoughts, opinions, experiments, and market notes.
      Nothing here is financial advice, medical advice, life advice, or any other kind of
      “you told me to YOLO my pension” advice.
    </p>

    <p class="disclaimer-modal__subhead"><strong>By continuing you confirm that:</strong></p>

    <ul class="disclaimer-modal__list">
      <li>You understand this site is for education / entertainment only.</li>
      <li>You’ll make your own decisions and take your own risks.</li>
      <li>You won’t treat anything here as a recommendation to buy, sell, or trade anything.</li>
      <li>You’re not going to come back later and say “but you said…”</li>
    </ul>

    <p class="disclaimer-modal__fine">If you don’t agree, please close this tab.</p>

    <div class="disclaimer-modal__actions">
      <button id="acceptDisclaimer" class="disclaimer-modal__primary" type="button">
        I Understand &amp; Agree
      </button>

      <a class="disclaimer-modal__secondary" href="about:blank" rel="nofollow noopener">
        I Don’t Agree
      </a>
    </div>
  </div>
</div>

<script>
(function () {
  var ACCEPT_KEY = "disclaimerAccepted:v1";
  var REDIRECT_KEY = "postDisclaimerRedirect";

  var button = document.getElementById("acceptDisclaimer");
  if (!button) return;

  button.addEventListener("click", function () {
    try { localStorage.setItem(ACCEPT_KEY, "true"); } catch (e) {}

    // cookie fallback scoped to this project site
    try {
      document.cookie =
        "disclaimerAccepted=v1; path={{ site.baseurl | default: '/' }}/; " +
        "max-age=31536000; samesite=lax";
    } catch (e2) {}

    var redirect = null;
    try {
      redirect = sessionStorage.getItem(REDIRECT_KEY);
      sessionStorage.removeItem(REDIRECT_KEY);
    } catch (e3) {}

    if (redirect) window.location.assign(redirect);
    else window.location.assign("{{ '/' | relative_url }}");
  });
})();
</script>
