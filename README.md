# React Auto Draft (@tahdeth/react-autodraft)

A lightweight, type-safe, and zero-dependency React hook for automatic form state persistence, recovery, and optional encryption using `localStorage`.

---

## Features

- **Zero Configuration Setup**: Automatically tracks input, textarea, and select changes without manual state binding.
- **Type-Safe**: Built with TypeScript with full support for modern React types.
- **Data Encryption**: Optional built-in Base64/URI encoding to secure sensitive user input in `localStorage`.
- **TTL (Time-To-Live)**: Automatically expire and clear drafts after a specified duration.
- **Draft Status Indicators**: Track real-time saving status and last saved timestamps.
- **Easy Cleanup**: Programmatically clear drafts upon successful form submission.

---

## Installation

Install the package via npm:

```bash
npm install @tahdeth/react-autodraft