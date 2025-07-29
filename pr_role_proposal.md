# PR Role Scope Reduction Proposal

## Current Problem

The original specification assigns PR an overly complex administrative role that creates unnecessary development overhead, introduces bias risks, and increases the likelihood of human errors during our tight 2-month delivery timeline.

## Proposed Changes

### **Remove from PR Role:**

#### 1. **Application Period Management**

- **Current**: PR manually sets start/end dates through dashboard
- **Proposed**: Developers configure periods in advance via database/config
- **Rationale**: Eliminates risk of incorrect dates breaking the system, reduces UI complexity

#### 2. **Manual Lottery Execution**

- **Current**: PR manually triggers lottery via dashboard button
- **Proposed**: Automated lottery execution via scheduled Cloud Function
- **Rationale**: Removes bias concerns, eliminates human error, ensures consistent timing

#### 3. **Manual Email Management**

- **Current**: PR manually sends lottery result notifications
- **Proposed**: Automatic email sending after lottery completion
- **Rationale**: Guarantees timely notifications, removes "forgot to send" risk

#### 4. **Shareholder Data Import via Dashboard**

- **Current**: PR uploads shareholder CSV through web interface
- **Proposed**: Python script monitors shared folder for CSV uploads
- **Rationale**: Eliminates upload format errors, reduces development complexity

#### 5. **User Activity & System Log Monitoring**

- **Current**: PR has access to detailed user operation logs
- **Proposed**: Remove entirely - unnecessary for PR functions
- **Rationale**: No business justification for PR to monitor technical logs

### **Retain for PR Role:**

#### 1. **Read-Only Dashboard Access**

PR maintains access to company-wide internal dashboard with:

- Real-time application statistics
- Lottery progress and results
- System status monitoring
- All data views are **read-only**

#### 2. **Report Generation**

- Download application summary CSV
- Download lottery results CSV
- Access to standard business reports

## Implementation Benefits

### **Development Efficiency**

- **~80% reduction** in PR-specific UI components
- **Eliminates complex role-based permissions** for sensitive operations
- **Reduces testing surface area** significantly

### **Operational Security**

- **Removes bias risks** from manual lottery execution
- **Eliminates human error** in critical processes
- **Reduces attack surface** by removing manual controls

### **Reliability Improvements**

- **Guaranteed email delivery** via automation
- **Consistent lottery timing** via scheduled execution
- **Error-free data imports** via script validation

## Technical Implementation

### **Automated Processes**

```
1. Lottery Execution: Cloud Function triggered on schedule
2. Email Notifications: Automatic after lottery completion
3. Data Import: Python script with shared folder monitoring
4. Period Management: Database configuration by developers
```

### **PR Dashboard Access**

```
- Company-wide statistics dashboard (read-only)
- Standard report downloads
- No administrative controls
- No sensitive system access
```

## Risk Mitigation

### **Concern**: "PR loses control over process"

**Response**: PR maintains full visibility through read-only dashboard while eliminating operational risks

### **Concern**: "What if automation fails?"

**Response**: Automated processes include monitoring, logging, and developer alerts. Manual override capabilities remain available to development team.

### **Concern**: "How do we handle edge cases?"

**Response**: CS team handles shareholder inquiries, development team handles technical issues. Clear escalation paths defined.

## Recommendation

Implement this simplified PR role to:

1. **Meet 2-month delivery timeline** with reduced complexity
2. **Improve system reliability** through automation
3. **Maintain PR oversight needs** via read-only dashboard access
4. **Eliminate bias and security concerns** from manual processes

This approach transforms PR from a complex system administrator into an informed stakeholder with appropriate visibility and reporting capabilities.
