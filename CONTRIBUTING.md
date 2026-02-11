# Contributing to PRISM

Thank you for your interest in contributing to **PRISM - Property, Rental, Income & Sales Manager**!

---

## 🎯 How to Contribute

### **Reporting Bugs**

Found a bug? Help us fix it!

1. **Check existing issues** - Search to see if it's already reported
2. **Create a new issue** with:
   - Clear title (e.g., "Payment calculation error for credits")
   - Browser & version (e.g., Chrome 120)
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots (if applicable)
   - Console errors (if any)

**Example:**
```
Title: Tenant balance shows incorrect amount

Browser: Chrome 120 on Windows 11

Steps:
1. Add tenant with ₱3,000/month rent
2. Tenant moves in Jan 1, 2026
3. Record ₱3,000 payment on Feb 1
4. Check balance

Expected: ₱0 (1 month paid)
Actual: ₱3,000 (shows as unpaid)

Console: No errors
Screenshot: [attached]
```

---

### **Suggesting Features**

Have an idea? We'd love to hear it!

1. **Open an issue** with label `feature-request`
2. **Describe the feature:**
   - What problem does it solve?
   - How would it work?
   - Who would benefit?
   - Examples of use cases

**Example:**
```
Title: Add email receipt feature

Problem: Users want to send payment receipts to tenants

Solution: Add "Email Receipt" button on payment confirmation

Benefits:
- Professional communication
- Automatic record keeping
- Tenant convenience

Use Case:
After recording ₱3,000 rent payment, click "Email Receipt"
to send PDF receipt to tenant's email.
```

---

### **Submitting Code**

Ready to code? Follow these steps:

#### **1. Fork & Clone**

```bash
# Fork on GitHub (click Fork button)
# Then clone your fork:
git clone https://github.com/YOUR_USERNAME/prism.git
cd prism
```

#### **2. Create Feature Branch**

```bash
git checkout -b feature/your-feature-name
# Examples:
# feature/sms-notifications
# fix/payment-calculation
# docs/improve-readme
```

#### **3. Make Changes**

**Code Style:**
- Use consistent indentation (4 spaces)
- Clear variable names
- Add comments for complex logic
- Follow existing patterns

**Testing:**
- Test your changes thoroughly
- Test on multiple browsers
- Test with sample data
- Test offline mode

#### **4. Commit Changes**

```bash
git add .
git commit -m "Add feature: SMS notifications for rent reminders"
```

**Commit Message Format:**
```
Add feature: [Brief description]
Fix: [Bug description]
Docs: [Documentation changes]
Style: [UI/formatting changes]
Refactor: [Code improvement]
```

#### **5. Push & Create PR**

```bash
git push origin feature/your-feature-name
```

Then on GitHub:
1. Click "New Pull Request"
2. Select your branch
3. Fill PR template
4. Submit!

**PR Template:**
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation
- [ ] Performance improvement

## Testing
- [ ] Tested on Chrome
- [ ] Tested on Firefox
- [ ] Tested offline mode
- [ ] Tested with sample data

## Screenshots (if applicable)
[Add screenshots]

## Checklist
- [ ] Code follows project style
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] No console errors
```

---

## 📋 Development Guidelines

### **File Structure**

```
prism/
├── index.html          # Main application (single file)
├── README.md           # Project documentation
├── LICENSE             # MIT License
├── CONTRIBUTING.md     # This file
├── .gitignore         # Git ignore rules
├── docs/              # Documentation files
│   ├── PAYMENT_METHODS_GUIDE.md
│   ├── AUTO_RESET_BEHAVIOR.md
│   ├── OFFLINE_CAPABILITY_GUIDE.md
│   └── ENTITY_ARCHITECTURE.md
└── screenshots/       # App screenshots (optional)
```

### **Code Sections in index.html**

1. **HTML Structure** (Lines 1-5100)
   - Meta tags
   - CSS styles
   - UI components
   - Modals

2. **JavaScript Core** (Lines 5100-6500)
   - IndexedDB setup
   - Firebase config
   - Theme system
   - PRISM Guardian

3. **Business Logic** (Lines 6500-18000)
   - CRUD functions
   - Payment processing
   - Calculations
   - Filtering/Search

4. **Helper Functions** (Lines 18000-end)
   - Utilities
   - Exports
   - Sample data

### **Key Functions to Know**

**Database Operations:**
```javascript
await dbAdd('storeName', object)      // Create
await dbGet('storeName', id)          // Read
await dbUpdate('storeName', object)   // Update
await dbDelete('storeName', id)       // Delete
await dbGetAll('storeName')           // Get all
await dbClear('storeName')            // Clear all
```

**UI Helpers:**
```javascript
showModal('modal-id')                 // Open modal
hideModal('modal-id')                 // Close modal
showToast(message, type)              // Show notification
setButtonLoading(btn, state)          // Loading state
```

**Data Sync:**
```javascript
syncToFirebase()                      // Sync to cloud
loadFromFirebase()                    // Load from cloud
```

---

## 🧪 Testing Checklist

Before submitting PR, test:

### **Basic Functionality**
- [ ] App loads without errors
- [ ] All sections accessible
- [ ] Dark/light theme toggle works
- [ ] Offline mode functional

### **CRUD Operations**
- [ ] Can create entries
- [ ] Can read/view details
- [ ] Can update entries
- [ ] Can delete entries

### **Payment Processing**
- [ ] Rent payments record correctly
- [ ] Credit payments calculate balance
- [ ] Balance updates immediately
- [ ] Auto-reset works (staff, credits)

### **Data Persistence**
- [ ] Data survives page reload
- [ ] Backup/restore works
- [ ] Clear all data works
- [ ] Sample data loads

### **Cross-Browser**
- [ ] Chrome/Edge
- [ ] Firefox
- [ ] Safari (if available)
- [ ] Mobile browsers

---

## 🎨 UI/UX Guidelines

### **Design Principles**

1. **Mobile First**
   - Design for small screens first
   - Use responsive units (rem, %, vw/vh)
   - Touch-friendly buttons (min 44px)

2. **Consistency**
   - Follow existing color scheme
   - Use standard button styles
   - Match icon usage patterns

3. **Accessibility**
   - Sufficient color contrast
   - Clear labels and placeholders
   - Keyboard navigation support

4. **Performance**
   - Minimize DOM operations
   - Use event delegation
   - Lazy load when possible

### **Color Palette**

```css
/* Light Theme */
--primary: #2563eb
--success: #10b981
--warning: #f59e0b
--danger: #ef4444
--bg-primary: #ffffff
--bg-secondary: #f9fafb
--text-primary: #111827
--text-secondary: #6b7280

/* Dark Theme */
--primary: #3b82f6
--bg-primary: #1f2937
--bg-secondary: #111827
--text-primary: #f9fafb
--text-secondary: #9ca3af
```

---

## 📝 Documentation

### **Code Comments**

**Good:**
```javascript
// Calculate total due including interest
const totalDue = principal + (principal * interestRate / 100);
```

**Better:**
```javascript
/**
 * Calculates total amount due for a credit/loan
 * @param {number} principal - Original loan amount
 * @param {number} interestRate - Interest rate percentage
 * @param {string} interestType - 'simple', 'flat', or 'none'
 * @returns {number} Total amount due
 */
function calculateTotalDue(principal, interestRate, interestType) {
    // Implementation
}
```

### **Updating Documentation**

When adding features, update:
- README.md (features list)
- Relevant guide in docs/
- Inline code comments
- This CONTRIBUTING.md if needed

---

## 🐛 Debugging Tips

### **Common Issues**

**IndexedDB Errors:**
```javascript
// Check browser support
if (!window.indexedDB) {
    console.error('IndexedDB not supported');
}

// Check for quota errors
try {
    await dbAdd('store', data);
} catch (error) {
    if (error.name === 'QuotaExceededError') {
        console.error('Storage quota exceeded');
    }
}
```

**Firebase Sync Issues:**
```javascript
// Check Firebase initialization
if (!firebaseReady) {
    console.error('Firebase not initialized');
}

// Check user authentication
if (!currentUser) {
    console.error('User not logged in');
}
```

**Modal Not Showing:**
```javascript
// Ensure modal ID is correct
const modal = document.getElementById('modal-id');
if (!modal) {
    console.error('Modal not found:', 'modal-id');
}
```

### **Browser DevTools**

**Console:**
- `[PRISM INFO]` - General information
- `[PRISM SUCCESS]` - Successful operations
- `[PRISM ERROR]` - Errors to investigate

**IndexedDB:**
1. Open DevTools (F12)
2. Application tab
3. IndexedDB → PRISM_DB
4. View stores and data

---

## 🎯 Priority Areas

We especially welcome contributions in:

1. **Bug Fixes** - Always appreciated!
2. **Performance** - Optimization improvements
3. **Documentation** - Clearer guides and examples
4. **Accessibility** - Better keyboard/screen reader support
5. **Internationalization** - Multi-language support
6. **Mobile UX** - Enhanced mobile experience

---

## ❓ Questions?

- **General Questions**: Open a GitHub Discussion
- **Bug Reports**: Open an Issue
- **Feature Ideas**: Open an Issue with `feature-request` label
- **Code Questions**: Comment on relevant PR/Issue

---

## 🏆 Recognition

Contributors will be:
- Listed in README.md
- Credited in release notes
- Appreciated in the community!

---

## 📜 Code of Conduct

### **Our Pledge**

We pledge to make participation in PRISM welcoming and harassment-free for everyone.

### **Our Standards**

**Positive behavior:**
- Using welcoming language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what's best for the community
- Showing empathy towards others

**Unacceptable behavior:**
- Trolling, insulting/derogatory comments
- Public or private harassment
- Publishing others' private information
- Other conduct inappropriate in a professional setting

---

## 🙏 Thank You!

Every contribution helps make PRISM better for everyone. Whether it's:
- 🐛 Reporting a bug
- 💡 Suggesting a feature
- 📝 Improving documentation
- 💻 Contributing code
- ⭐ Starring the repository

**Thank you for being part of PRISM!**

---

**Happy Coding! 🚀**

*Built with ❤️ by OMNIGRID ONLINE*
