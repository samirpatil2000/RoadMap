## Git Commit & Branch Naming Conventions

### ✅ Commit Message Types
- **[FEAT]** – New feature (e.g., adding support for storing user data in `useAtom`)  
- **[FIX]** – Bug fix (e.g., settings page organisation loading issue in new tab)  
- **[REF]** – Refactor code (no functional changes, just structure/optimisation)  
- **[NEW-UI]** – Introduce a completely new UI page/component (e.g., new login page)  
- **[REF-UI]** – UI refactor/improvement (e.g., improve login page UI)  

⚡️ (Optional additional tags)  
- **[DOCS]** – Documentation changes  
- **[CHORE]** – Build, tooling, or dependency updates  
- **[TEST]** – Test-related changes  

---

### ✅ Branch Naming Conventions
- **feature/** – For new features (e.g., `feature/add-user-data-storage`)  
- **fix/** – For bug fixes (e.g., `fix/settings-page-loading`)  
- **hotfix/** – For urgent production fixes (e.g., `hotfix/login-crash`)  
- **ref/** – For refactoring (e.g., `ref/cleanup-auth-hooks`)  
- **revamp/** – For large-scale redesigns or major changes (e.g., `revamp/ui-overhaul`)  

⚡️ (Optional additional branch types)  
- **docs/** – For documentation-only branches  
- **test/** – For test-specific branches  

---

### ✅ Example Usage
**Commit Message:**  
```
[FEAT] Add support for storing user data in useAtom
```

**Branch Name:**  
```
feature/add-user-data-storage
```
