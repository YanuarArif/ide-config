# MiniMax Universal Workflow & Setup Instructions

## Overview
This document provides universal instructions for debugging, fixing, and maintaining code changes with proper version control. Apply this workflow to any coding task, regardless of technology stack or specific problem domain.

## 🗂️ Standard File Organization Structure

### Directory Layout
```
workspace/
├── source-project/                   # SOURCE CODE (apply latest fixes here)
│   └── [your-project-structure]/
│       ├── component1.tsx
│       └── component2.tsx
└── file-change/                      # VERSION HISTORY
    ├── component1-v1.tsx             # Previous fixes
    ├── component1-v2.tsx             # Latest fixes
    ├── component2-v1.tsx
    ├── component2-v2.tsx
    ├── notes-v1.md                   # Investigation notes
    ├── notes-v2.md                   # Applied fixes
    └── README.md                     # Master documentation
```

### Version Control Naming Convention
- **Format**: `filename-v{version}.{extension}`
- **Example**: `UserComponent-v1.tsx`, `UserComponent-v2.tsx`
- **Never**: `filename.tsx-v1` (incorrect format)
- **Master files**: `README.md` (current solution), `notes-v{version}.md` (version-specific)

## 🔄 Complete Universal Workflow

### Phase 1: Problem Understanding & Investigation
1. **Problem Analysis**
   - Understand user's issue description
   - Identify symptoms vs expected behavior
   - Determine scope (frontend vs backend vs both)
   - Note any error messages or logs

2. **Code Investigation**
   - Locate relevant files using `glob` and `grep`
   - Read key files to understand implementation
   - Use specific line ranges for focused review
   - Identify dependencies and relationships between components

3. **Initial Setup**
   ```bash
   mkdir -p /workspace/file-change
   echo "# Investigation Notes - Version 1" > /workspace/file-change/notes-v1.md
   ```

### Phase 2: Solution Development & Implementation
1. **Solution Planning**
   - List all files requiring modifications
   - Prioritize fixes (critical vs enhancement)
   - Identify potential dependencies between fixes
   - Plan testing approach

2. **Implementation Process**
   - Apply fixes incrementally to source code
   - Test each change before moving to next
   - Document changes as you make them
   - Maintain backup of previous working state

3. **Version Control Management**
   - **V1**: Initial state or basic fixes
   - **V2**: Major fixes or fundamental changes
   - **V3+**: Additional improvements or edge cases

4. **Creating Version Files**
   ```bash
   # Save initial state
   cp source-project/path/file.tsx file-change/file-v1.tsx
   
   # Apply and save fix
   # ... make changes to source code ...
   cp source-project/path/file.tsx file-change/file-v2.tsx
   ```

### Phase 3: Documentation & Validation
1. **Documentation Creation**
   - Create comprehensive README.md
   - Document all changes with before/after examples
   - Explain technical reasoning
   - Include version history

2. **Testing & Validation**
   - Verify source code has latest changes
   - Test new functionality thoroughly
   - Ensure existing features still work
   - Document any remaining issues

## 🛠️ Universal Code Change Patterns

### Common Debugging Approaches
1. **State Management Issues**
   - Check initialization values
   - Verify state synchronization
   - Examine event handlers and callbacks
   - Look for race conditions

2. **Form Handling**
   - Validate form schema matches UI
   - Check field registration with form library
   - Ensure proper data flow
   - Verify submission handling

3. **Component Communication**
   - Check prop drilling issues
   - Verify callback functions
   - Examine context usage
   - Look for event propagation

4. **API Integration**
   - Verify API endpoints
   - Check request/response handling
   - Examine error states
   - Test async operations

### Universal Debugging Commands
```bash
# Find patterns across all files
grep -r "problematic-pattern" /workspace/

# Check specific function calls
grep -n "functionName(" filename.tsx

# Find all component references
grep -r "ComponentName" /workspace/

# Locate specific styles or classes
grep -n "className\|style" filename.tsx
```

## 🔍 Investigation Techniques

### File Analysis Strategy
1. **Start with Entry Points**
   - Find main components/pages
   - Identify routing logic
   - Locate data flow sources

2. **Trace Data Flow**
   - Follow state changes
   - Track prop drilling
   - Identify data transformations
   - Map event handling chains

3. **Component Hierarchy**
   - Map parent-child relationships
   - Identify shared components
   - Locate re-used logic

### Code Reading Approach
```bash
# Read specific sections
Read file_path with limit=20, offset=100

# Examine entire files for understanding
Read file_path

# Search for specific patterns
grep pattern file_path
```

## 📝 Universal Documentation Template

### README.md Structure
```markdown
# [Issue Type] Fix - VERSION X

## Problem Summary
Clear description of the issue affecting [system/component]

## Investigation Process
1. [Step 1] - What was discovered
2. [Step 2] - Root cause identification
3. [Step 3] - Solution approach

## Root Causes & Solutions

### CRITICAL FIX 1: [Issue Name]
**File**: `path/to/file.tsx`
**Problem**: [What was wrong]

**Before**:
```typescript
// problematic code
```

**After**:
```typescript
// fixed code
```

### ENHANCEMENT FIX 2: [Issue Name]
**File**: `path/to/file2.tsx`
**Problem**: [Secondary issue]

**Solution**: [How it was fixed]

## Technical Explanation
[Why the fix works and what it addresses]

## Files Modified
1. **file1.tsx** - [change summary]
2. **file2.tsx** - [change summary]

## Testing Instructions
1. **Setup**: [prerequisites]
2. **Test Case 1**: [steps and expected result]
3. **Test Case 2**: [steps and expected result]

## Expected Results
- ✅ [Specific outcome 1]
- ✅ [Specific outcome 2]
- ✅ [Specific outcome 3]

## Version History
- **V1**: [initial findings]
- **V2**: [major fixes]
- **V3**: [additional improvements]
```

## 🚀 Quick Start Templates

### New Task Request Template
```
"Please help me debug [general issue description]. 

I need you to follow the minimax.md universal workflow:
1. Create /workspace/file-change/ directory
2. Use version suffixes (-v1, -v2, etc.) for different fix iterations
3. Apply final fixes to source code in source-project/
4. Create comprehensive README.md documentation
5. Provide testing instructions

Context:
- Project: [description]
- Problem: [specific issue]
- Expected: [what should happen]
- Current: [what actually happens]

Files to investigate: [list relevant files]"
```

### Issue Analysis Template
```
Problem: [description]
Symptoms: [what user sees]
Expected: [what should happen]
Current: [what happens instead]
Scope: [frontend/backend/full-stack]
```

## ⚡ Universal Quality Checklist

Before task completion:
- [ ] file-change directory exists with proper version naming
- [ ] All fixes applied to source code
- [ ] Version files created for all modified files
- [ ] README.md contains comprehensive documentation
- [ ] Before/after code examples included
- [ ] Technical explanation provided
- [ ] Testing instructions clear and complete
- [ ] Expected results documented
- [ ] Version history maintained
- [ ] Source code verified to have latest changes

## 🔧 Universal File Operations

### Standard Commands
```bash
# Setup
mkdir -p /workspace/file-change

# Version management
mv file.tsx file-v1.tsx
cp source-project/file.tsx file-v2.tsx

# Verification
grep -n "specific-fix" source-project/file.tsx
ls -la /workspace/file-change/
```

### File Management Rules
1. **Always read before writing**
   ```bash
   Read file_path
   Edit file_path
   ```

2. **Use MultiEdit for multiple changes**
   ```bash
   MultiEdit file_path with edits
   ```

3. **Create version backups**
   ```bash
   cp file file-v1.tsx
   # make changes
   cp file file-v2.tsx
   ```

## 📚 Universal Patterns by Technology

### React/Next.js Applications
- Check component state management
- Verify prop drilling and context usage
- Examine useEffect dependencies
- Test form handling with react-hook-form
- Validate API integration patterns

### Backend Applications
- Examine request/response handling
- Check database connection patterns
- Verify middleware usage
- Test async operation handling
- Validate error handling

### Database Issues
- Check schema definitions
- Verify query syntax
- Examine connection pooling
- Test transaction handling
- Validate data type conversions

### API Integration
- Verify endpoint configurations
- Check authentication headers
- Test error response handling
- Examine timeout configurations
- Validate data parsing

## 🆘 Emergency Debugging Commands

```bash
# Universal search patterns
grep -r "TODO\|FIXME\|BUG\|HACK" /workspace/
grep -rn "console.log\|debugger" /workspace/

# File structure analysis
find /workspace -name "*.tsx" -o -name "*.ts" -o -name "*.js" | head -20
ls -la /workspace/file-change/

# Check for common issues
grep -rn "undefined\|null" source-project/ | grep -v node_modules
```

## 💡 Key Principles

1. **Systematic Investigation**: Always understand the problem before attempting fixes
2. **Version Control**: Maintain history of all changes with proper naming
3. **Incremental Testing**: Test each change before proceeding to next
4. **Comprehensive Documentation**: Document everything for future reference
5. **Universal Application**: Apply these patterns regardless of technology stack

## 📝 Usage Example

### For Any New Debugging Task:
Copy this section to your new conversation:

```
"I need help debugging [your issue]. 

Please use the minimax.md universal workflow:
1. Create file-change/ directory with version suffixes
2. Investigate the problem systematically
3. Apply fixes to source code
4. Maintain version history
5. Document everything in README.md

My specific situation:
- Problem: [describe issue]
- System: [technology stack]
- Expected behavior: [what should happen]
- Current behavior: [what actually happens]"
```

---

**Created**: 2025-11-14 16:35:50  
**Updated**: 2025-11-14 16:35:50  
**Author**: MiniMax Agent  
**Purpose**: Universal workflow for any debugging/development task