# User Management UI Specification

## 1. Overview
This document describes the user interface and behavior of the User Management screen. The purpose of this screen is to allow administrators to view, create, edit, enable/disable, and manage user roles.

---

## 2. Page Layout

The screen is divided into two main sections:

### 2.1 Left Panel – User List
- Displays all users in a table format
- Columns:
  - ID
  - User Name
  - Email
  - Enabled (true/false)

### 2.2 Right Panel – User Form
- Used for creating or editing a user
- Contains input fields and actions

---

## 3. Top Actions

### 3.1 New User Button
- Label: `+ New User`
- Action:
  - Clears the form
  - Switches form to "Create Mode"

### 3.2 Hide Disabled User Checkbox
- Default: unchecked
- When checked:
  - Filters out users where Enabled = false

### 3.3 Save User Button
- Saves the current form
- Behavior:
  - If creating → adds new user
  - If editing → updates existing user

---

## 4. User Table Behavior

- Clicking a row:
  - Loads user data into the form
  - Switches form to "Edit Mode"
- Sorting:
  - Columns should be sortable
- Filtering:
  - Based on "Hide Disabled User"

---

## 5. User Form Fields

### 5.1 Username
- Required
- Must be unique

### 5.2 Display Name
- Required

### 5.3 Phone
- Optional
- Should validate phone format

### 5.4 Email
- Required
- Must be valid email format

### 5.5 User Roles
- Multi-select dropdown
- Options:
  - Guest
  - Admin
  - SuperAdmin
- At least one role must be selected

### 5.6 Enabled
- Checkbox
- Default: true

---

## 6. Form Behavior

### 6.1 Create Mode
- Empty fields
- Enabled = true by default

### 6.2 Edit Mode
- Fields pre-filled with selected user data

### 6.3 Validation
- Show inline error messages:
  - Missing required fields
  - Invalid email format
  - No role selected

---

## 7. Save Behavior

- On Save:
  - Validate all fields
  - If valid:
    - Save to backend
    - Refresh user list
    - Show success message
  - If invalid:
    - Prevent submission
    - Highlight errors

---

## 8. Initial State

When the page loads:
- User list is displayed
- No user is selected
- Form is empty (Create Mode)
- Enabled checkbox is checked

---

## 9. Error Handling

- Network errors:
  - Show error notification
- Validation errors:
  - Display inline messages

---

## 10. UX Considerations

- Responsive layout
- Clear visual feedback on selection
- Disabled users visually distinguishable (e.g., greyed out)
- Loading indicator during save

---

## 11. Security Considerations

- Only authorized users (admins) can access this page
- Role assignment should be restricted based on permissions
