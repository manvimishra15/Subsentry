## 🧾 Issue 7: Fetch Subscriptions API (GET)

### ✨ Expanded Description
This issue enables users to retrieve **only their own subscriptions** from the backend. It powers the dashboard listing and must return clean, predictable JSON responses.

---

### ✅ Endpoint to Implement
**GET** `/api/subscriptions`

Returns all subscriptions **belonging to the currently authenticated user**.

---

### 🎯 Why this issue exists
- Forms the backbone of the dashboard
- Teaches safe, user‑scoped data retrieval
- Prevents accidental data leaks across users

---

### ✅ Key Expectations
- User‑based filtering (only current user’s subscriptions)
- Stable, readable response structure
- Appropriate HTTP status codes and error handling
- Clean separation of route + controller logic

---

### ❌ What NOT to do
- Do **not** return subscriptions for other users
- Do **not** trust client‑provided user IDs
- Do **not** over‑fetch unnecessary fields

---

### 🧪 Testing Expectations
Contributors should be able to show:
- Only the authenticated user’s data is returned
- Proper response when user is unauthenticated

---

### 📁 Workspace Rule (Mandatory)
Only make changes inside your own folder:

```
subsentry/
└── contributors/
    └── your_folder/
```
