# Usage Guide (@tahdeth/react-autodraft)

This guide covers common use cases, advanced configurations, and best practices for `@tahdeth/react-autodraft`.

---

## Table of Contents
1. [Basic Form Handling](#basic-form-handling)
2. [Handling Checkboxes and Radios](#handling-checkboxes-and-radios)
3. [Using TTL (Expiration Logic)](#using-ttl-expiration-logic)
4. [Securing Data with Encryption](#securing-data-with-encryption)
5. [Real-time Status and Indicators](#real-time-status-and-indicators)

---

## 1. Basic Form Handling
To attach auto-draft capabilities to a standard form, pass a unique `formId` and bind the `formRef` to your `<form>` element.

```tsx
import { useAutoDraft } from '@tahdeth/react-autodraft';

function SimpleForm() {
  const { formRef, clearDraft } = useAutoDraft({ formId: 'simple-signup' });

  return (
    <form ref={formRef} onSubmit={(e) => { e.preventDefault(); clearDraft(); }}>
      <input name="username" placeholder="Username" />
      <input name="email" placeholder="Email" />
      <button type="submit">Register</button>
    </form>
  );
}




2. Handling Checkboxes and Radios
The library automatically monitors native HTML elements including text inputs, textareas, select dropdowns, checkboxes, and radio buttons based on their name attributes.

import { useAutoDraft } from '@tahdeth/react-autodraft';

function SurveyForm() {
  const { formRef } = useAutoDraft({ formId: 'survey-form' });

  return (
    <form ref={formRef}>
      <label>
        <input type="checkbox" name="subscribe" /> Subscribe to newsletter
      </label>
      
      <div>
        <label><input type="radio" name="gender" value="male" /> Male</label>
        <label><input type="radio" name="gender" value="female" /> Female</label>
      </div>
    </form>
  );
}

3. Using TTL (Expiration Logic)
If you want drafts to automatically expire after a specific duration (e.g., 30 minutes), pass ttl in milliseconds.

const { formRef } = useAutoDraft({
  formId: 'temporary-form',
  ttl: 30 * 60 * 1000, // 30 minutes in milliseconds
});

4. Securing Data with Encryption
To prevent sensitive information from being stored in plain text inside localStorage, enable encryption.

const { formRef } = useAutoDraft({
  formId: 'secure-checkout',
  encrypt: true, // Encrypts JSON payload using Base64/URI encoding
});


5. Real-time Status and Indicators
You can track whether changes are successfully saved and show the last saved timestamp to the user.

import { useAutoDraft } from '@tahdeth/react-autodraft';

function StatusForm() {
  const { formRef, isSaved, lastSaved, clearDraft } = useAutoDraft({
    formId: 'status-form',
  });

  return (
    <div>
      <div style={{ fontSize: '12px', color: isSaved ? 'green' : 'gray' }}>
        {isSaved ? 'All changes saved' : 'Saving...'}
        {lastSaved && ` at ${lastSaved.toLocaleTimeString()}`}
      </div>

      <form ref={formRef}>
        <textarea name="notes" placeholder="Type notes here..." />
        <button type="button" onClick={clearDraft}>Clear Draft</button>
      </form>
    </div>
  );
}

