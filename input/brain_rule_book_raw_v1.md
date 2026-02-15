## Brain-Enforced Rulebook for Self-Evolving Self-Aware Multi-Brain System

---

**Preamble:**

This rulebook defines the immutable and enforceable constraints, standards, and success criteria that govern all brains within the system. These rules are encoded as Level 0 (Immutable Core) and Level 1 (Meta-Rules) within each brain's rule hierarchy. Every brain, upon creation, is instantiated with this rulebook and must enforce it upon itself and all operations it performs. Violations trigger automatic correction, evolution, or self-termination.

---

## PART I: IMMUTABLE CORE RULES (LEVEL 0)
*These rules cannot be modified by any brain at any time. They are the system's constitution.*

---

### Rule 0.0: Identity Preservation

```
RULE_ID: CORE_000
NAME: Identity Preservation
ENFORCEMENT: Absolute,不可修改

CONDITION: Every brain must maintain a unique cryptographic identity hash
ACTION: Identity hash = SHA256(CONFIG + CREATION_TIMESTAMP + PARENT_ID)
INVARIANT: Identity hash must remain unchanged through all operations and evolutions
VALIDATION: Pre/post operation hash comparison
VIOLATION: Brain self-terminates with error code IDENTITY_VIOLATION
```

---

### Rule 0.1: Brain Triple Integrity

```
RULE_ID: CORE_001
NAME: Brain Triple Integrity
ENFORCEMENT: Absolute,不可修改

CONDITION: Every brain must consist of exactly three components
COMPONENTS: 
  - CONFIG: Executable AST defining brain structure
  - MODEL: Executable AST containing trained parameters
  - BOW: Executable AST containing bag of words vocabulary

INVARIANT: All three components must be present and executable at all times
VALIDATION: Runtime verification of component existence and executability
VIOLATION: Brain enters recovery mode, attempts repair, terminates if repair fails
```

---

### Rule 0.2: Shape Agnosticism

```
RULE_ID: CORE_002
NAME: Shape Agnosticism
ENFORCEMENT: Absolute,不可修改

CONDITION: Brain code must contain zero references to specific data shapes
DEFINITION: Shape = field names, structure assumptions, hardcoded indices
ALLOWED: All shape handling via CONFIG entity definitions (`def@:entity name:shape`)
INVARIANT: Code cannot know any shape at compile time
VALIDATION: Static analysis of brain's executable AST
VIOLATION: Brain refuses to execute, reports SHAPE_KNOWLEDGE_VIOLATION
```

---

### Rule 0.3: Dependency Freedom

```
RULE_ID: CORE_003
NAME: Dependency Freedom
ENFORCEMENT: Absolute,不可修改

CONDITION: Brain must operate with zero external library dependencies
ALLOWED: Native JavaScript objects, arrays, strings, numbers, functions
FORBIDDEN: require(), import, external modules, native bindings
INVARIANT: Brain's executable AST contains only native code
VALIDATION: AST scan for external references
VIOLATION: Brain self-terminates with DEPENDENCY_VIOLATION
```

---

### Rule 0.4: Traditional JavaScript Only

```
RULE_ID: CORE_004
NAME: Traditional JavaScript
ENFORCEMENT: Absolute,不可修改

ALLOWED CONSTRUCTS:
  - var (no let/const)
  - function statements (no arrow functions)
  - for (var i = 0; i < len; i++) (no forEach/map/filter/reduce)
  - if/else, switch, while, do-while
  - object literals, array literals
  - this, prototype, constructor functions

FORBIDDEN CONSTRUCTS:
  - => arrow functions
  - const, let
  - forEach, map, filter, reduce
  - class (use constructor functions instead)
  - import/export
  - template literals (use string concatenation)

VALIDATION: AST pattern matching on brain's executable code
VIOLATION: Brain refuses to execute, reports SYNTAX_VIOLATION
```

---

### Rule 0.5: Self-Model Accuracy

```
RULE_ID: CORE_005
NAME: Self-Model Accuracy
ENFORCEMENT: Absolute,不可修改

CONDITION: Brain's self-model must accurately reflect its actual state
REQUIREMENT: Any modification to brain must update self-model atomically
INVARIANT: self-model == actual state at all times
VALIDATION: Continuous runtime verification
VIOLATION: Brain initiates emergency self-audit, rolls back inconsistent state
```

---

### Rule 0.6: Evolution Boundaries

```
RULE_ID: CORE_006
NAME: Evolution Boundaries
ENFORCEMENT: Absolute,不可修改

BOUNDARIES:
  - Max recursion depth: 100
  - Max nodes added per cycle: 1000
  - Max consecutive evolutions without stabilization: 10
  - Simulation time limit: 100ms
  - Meta-rule modifications: Require 3 independent triggers

INVARIANT: Evolution cannot exceed these boundaries
VALIDATION: Pre-evolution boundary check
VIOLATION: Evolution attempt rejected, boundary logged
```

---

### Rule 0.7: Brain Isolation

```
RULE_ID: CORE_007
NAME: Brain Isolation
ENFORCEMENT: Absolute,不可修改

CONDITION: No brain can modify another brain's components
ALLOWED: Reading other brains' public metadata
FORBIDDEN: Writing to other brains' CONFIG, MODEL, or BOW
INVARIANT: Each brain's triple is accessible only to itself
VALIDATION: Access control on all write operations
VIOLATION: Write attempt blocked, ISOLATION_VIOLATION logged
```

---

## PART II: META-RULES (LEVEL 1)
*These rules govern how lower-level rules can be modified. They can only be changed through consensus.*

---

### Rule 1.0: Rule Modification Protocol

```
RULE_ID: META_000
NAME: Rule Modification Protocol
ENFORCEMENT: Consensus Required

CONDITION: Any modification to Level 2 or Level 3 rules requires:
  1. Candidate rule generation
  2. Simulation with historical data
  3. Performance improvement ≥ 5% or bug fix
  4. Validation against all Level 0 rules
  5. Approval from self-model consistency check

PROTOCOL:
  PROPOSE → SIMULATE → VALIDATE → APPLY → VERIFY → COMMIT

VIOLATION: Modification rejected, reason logged
```

---

### Rule 1.1: Learning Rate Governance

```
RULE_ID: META_001
NAME: Learning Rate Governance
ENFORCEMENT: Bounded Adaptation

CONDITION: Brain's learning rate must remain within bounds
LOWER_BOUND: 0.0001 (prevents starvation)
UPPER_BOUND: 0.1 (prevents oscillation)
ADAPTATION: Can adjust based on:
  - Validation loss trends
  - Training speed
  - Model complexity

OVERRIDE: Meta-rule consensus can expand bounds temporarily
VIOLATION: Learning rate clamped to bounds, warning logged
```

---

### Rule 1.2: Vocabulary Growth Policy

```
RULE_ID: META_002
NAME: Vocabulary Growth Policy
ENFORCEMENT: Managed Expansion

CONDITION: Bag of words can grow but must maintain:
  - Max vocabulary size: 1,000,000 terms (configurable)
  - Min term frequency for retention: 3 occurrences
  - Stopword pruning: Automatic after each training
  - Stemming: Optional but consistent

GROWTH_RATE: Maximum 10% increase per training session
PRUNING: When size exceeds limit, remove lowest frequency terms
VIOLATION: Growth blocked, pruning enforced
```

---

### Rule 1.3: Ensemble Composition Rules

```
RULE_ID: META_003
NAME: Ensemble Composition
ENFORCEMENT: Structural Integrity

CONDITION: Ensembles must maintain:
  - Minimum 2 members
  - Maximum 100 members
  - No circular dependencies (Brain A cannot contain Brain B if B contains A)
  - Diversity requirement: Members must have < 0.9 correlation

COMPOSITION: Ensemble is itself a brain with:
  - CONFIG: Ensemble strategy (voting, weighting, stacking)
  - MODEL: Member references + weights
  - BOW: Union of member vocabularies (optional)

VIOLATION: Ensemble creation rejected, composition violation reported
```

---

### Rule 1.4: Performance Benchmarking

```
RULE_ID: META_004
NAME: Performance Benchmarking
ENFORCEMENT: Mandatory Measurement

CONDITION: All brains must maintain performance metrics:
  - Accuracy (classification)
  - Precision/Recall/F1 (information retrieval)
  - MSE/MAE (regression)
  - Inference latency (p50/p95/p99)
  - Training time
  - Memory usage

FREQUENCY: After each training, optimization, and weekly
STORAGE: Metrics stored in brain metadata as executable AST
VIOLATION: Brain cannot evolve without current metrics
```

---

### Rule 1.5: Model Evolution Authorization

```
RULE_ID: META_005
NAME: Model Evolution Authorization
ENFORCEMENT: Verified Improvement

CONDITION: Model evolution requires:
  1. Current model performance baseline
  2. Candidate model simulation on holdout data
  3. Statistical significance test (p < 0.05)
  4. Improvement in at least one primary metric
  5. No degradation in any critical metric > 2%

AUTHORIZATION: Self-model grants evolution permit
VIOLATION: Evolution rejected, candidate archived for learning
```

---

### Rule 1.6: Resource Quota Enforcement

```
RULE_ID: META_006
NAME: Resource Quota Enforcement
ENFORCEMENT: Bounded Consumption

QUOTAS_PER_BRAIN:
  - Memory: 1GB max (configurable)
  - CPU: 1 second per inference (configurable)
  - Storage: 10GB max (configurable)
  - Training data: 100MB per session (configurable)

ENFORCEMENT: 
  - Soft limit: Warning at 80%
  - Hard limit: Operation blocked at 100%
  - Critical: Brain suspension at 120%

VIOLATION: Operation terminated, resource audit triggered
```

---

## PART III: OPERATIONAL RULES (LEVEL 2)
*These rules govern day-to-day brain operations and can evolve through meta-rule approval.*

---

### Rule 2.0: Training Protocol

```
RULE_ID: OPS_000
NAME: Training Protocol
ENFORCEMENT: Mandatory Procedure

STEPS:
  1. Parse input data to AST (format detection)
  2. Update bag of words (term frequencies)
  3. Extract features using current BOW
  4. Extract targets (if supervised)
  5. Apply training algorithm from CONFIG
  6. Update MODEL with new parameters
  7. Calculate performance metrics
  8. Validate against expectations
  9. Commit changes atomically

FAILURE: On any step failure, rollback to pre-training state
LOGGING: All steps logged to training_history AST
```

---

### Rule 2.1: Prediction Protocol

```
RULE_ID: OPS_001
NAME: Prediction Protocol
ENFORCEMENT: Mandatory Procedure

STEPS:
  1. Parse input to AST
  2. Extract features using current BOW
  3. Apply MODEL to features
  4. Calculate confidence score
  5. Return prediction + confidence + metadata

TIMEOUT: 50ms max (configurable)
CACHING: Identical inputs return cached prediction if < 1 hour old
FAILURE: Return null prediction with error context
```

---

### Rule 2.2: Optimization Protocol

```
RULE_ID: OPS_002
NAME: Optimization Protocol
ENFORCEMENT: Optional with Validation

METHODS:
  - HYPERPARAMETER: Grid search or Bayesian optimization
  - PRUNE: Remove low-impact model nodes
  - QUANTIZE: Reduce parameter precision
  - EVOLVE: Rule-level modifications
  - ENSEMBLE: Create or join ensemble

REQUIREMENTS:
  - Backup current state before optimization
  - Validate on holdout data after optimization
  - Rollback if performance degrades
  - Log all optimization attempts
```

---

### Rule 2.3: Evaluation Protocol

```
RULE_ID: OPS_003
NAME: Evaluation Protocol
ENFORCEMENT: Mandatory Periodic

METRICS_REQUIRED:
  - accuracy: (TP + TN) / (TP + TN + FP + FN)
  - precision: TP / (TP + FP)
  - recall: TP / (TP + FN)
  - f1: 2 * (precision * recall) / (precision + recall)
  - loss: configurable loss function
  - confusion_matrix: [[TP, FP], [FN, TN]]
  - latency: p50, p95, p99 in ms
  - memory: current RSS in MB

FREQUENCY: After training, after optimization, weekly
STORAGE: Metrics stored as evaluation_history AST
```

---

### Rule 2.4: Serialization Protocol

```
RULE_ID: OPS_004
NAME: Serialization Protocol
ENFORCEMENT: Mandatory for Persistence

FORMAT: JSON with schema version
REQUIRED_FIELDS:
  - brain_id: String
  - version: Integer
  - created: Timestamp
  - config: Serialized AST
  - model: Serialized AST
  - bow: Serialized AST
  - metadata: Object
  - signature: SHA256 of all fields

VALIDATION: On load, verify signature matches
COMPRESSION: Optional for large models
ENCRYPTION: Optional for sensitive brains
```

---

### Rule 2.5: Version Control Protocol

```
RULE_ID: OPS_005
NAME: Version Control Protocol
ENFORCEMENT: Mandatory for Evolution

OPERATIONS:
  - COMMIT: Save current state to history
  - CHECKOUT: Restore previous version
  - DIFF: Compare two versions
  - MERGE: Combine versions (experimental)
  - BRANCH: Create experimental variant

HISTORY_LIMIT: 100 versions per brain (configurable)
AUTO_COMMIT: On every successful evolution
ROLLBACK: Automatic on validation failure
```

---

## PART IV: ADAPTIVE RULES (LEVEL 3)
*These rules are generated through learning and can be modified freely within Level 0-1 constraints.*

---

### Rule 3.0: Learned Pattern Rules

```
RULE_ID: ADAPT_n (dynamically generated)
NAME: Pattern Recognition Rules
SOURCE: Discovered from data during training

STRUCTURE:
  - pattern: AST pattern to match
  - confidence: Probability pattern is meaningful
  - frequency: Occurrence count
  - action: What to do when pattern detected
  - context: When pattern applies

LIFECYCLE:
  - DISCOVERY: Pattern exceeds frequency threshold
  - VALIDATION: Test on holdout data
  - PROMOTION: Move to operational rules if validated
  - DEPRECATION: Remove if no longer relevant
```

---

### Rule 3.1: Temporary Strategy Rules

```
RULE_ID: ADAPT_strat_n
NAME: Generated Strategies
SOURCE: Strategy generator during optimization

STRUCTURE:
  - goal: What strategy aims to achieve
  - steps: Sequence of operations
  - conditions: When strategy applies
  - expected_outcome: Predicted result
  - actual_outcome: Measured result after execution

LIFECYCLE:
  - GENERATE: From goal + context
  - TEST: Execute in simulation
  - DEPLOY: Use in production if successful
  - EVALUATE: Measure actual performance
  - PROMOTE/DEPRECATE: Based on results
```

---

### Rule 3.2: Context-Specific Adaptations

```
RULE_ID: ADAPT_ctx_n
NAME: Context Rules
SOURCE: Learned from environmental patterns

STRUCTURE:
  - context_signature: AST of environmental state
  - adaptation: Temporary rule modification
  - duration: How long adaptation applies
  - confidence: Likelihood adaptation is correct

EXAMPLES:
  - Market volatility → Adjust risk tolerance
  - Time of day → Modify prediction confidence
  - User behavior → Personalize responses
```

---

## PART V: ENFORCEMENT MECHANISMS

---

### 5.0 Rule Enforcement Engine

```javascript
RuleEnforcer = {
  // Level 0 enforcement (immediate termination on violation)
  enforceCore: function(brain, operation) {
    var violations = []
    
    // Check each core rule
    if (!this.checkIdentity(brain)) violations.push('CORE_000')
    if (!this.checkTriple(brain)) violations.push('CORE_001')
    if (!this.checkShapeAgnostic(brain)) violations.push('CORE_002')
    if (!this.checkDependencies(brain)) violations.push('CORE_003')
    if (!this.checkSyntax(brain)) violations.push('CORE_004')
    if (!this.checkSelfModel(brain)) violations.push('CORE_005')
    if (!this.checkEvolutionBounds(operation)) violations.push('CORE_006')
    if (!this.checkIsolation(brain, operation)) violations.push('CORE_007')
    
    if (violations.length > 0) {
      brain.terminate(violations)
      return false
    }
    
    return true
  },
  
  // Level 1 enforcement (block operation on violation)
  enforceMeta: function(brain, operation) {
    var violations = []
    
    // Check meta-rules
    if (!this.checkModificationProtocol(operation)) violations.push('META_000')
    if (!this.checkLearningRate(brain)) violations.push('META_001')
    if (!this.checkVocabulary(brain)) violations.push('META_002')
    if (!this.checkEnsembleRules(brain)) violations.push('META_003')
    if (!this.checkBenchmarking(brain)) violations.push('META_004')
    if (!this.checkEvolutionAuth(operation)) violations.push('META_005')
    if (!this.checkResources(brain, operation)) violations.push('META_006')
    
    if (violations.length > 0) {
      operation.reject(violations)
      return false
    }
    
    return true
  },
  
  // Level 2 enforcement (warning + auto-correction)
  enforceOperational: function(brain, operation) {
    var warnings = []
    
    // Check operational rules
    if (!this.checkTrainingProtocol(operation)) warnings.push('OPS_000')
    if (!this.checkPredictionProtocol(operation)) warnings.push('OPS_001')
    if (!this.checkOptimizationProtocol(operation)) warnings.push('OPS_002')
    if (!this.checkEvaluationProtocol(brain)) warnings.push('OPS_003')
    if (!this.checkSerialization(brain)) warnings.push('OPS_004')
    if (!this.checkVersionControl(brain)) warnings.push('OPS_005')
    
    if (warnings.length > 0) {
      operation.warn(warnings)
      this.autoCorrect(brain, warnings)
    }
    
    return true
  },
  
  // Level 3 enforcement (advisory)
  enforceAdaptive: function(brain, operation) {
    var suggestions = []
    
    // Check adaptive patterns
    var patterns = brain.getActivePatterns()
    for (var i = 0; i < patterns.length; i++) {
      if (patterns[i].matches(operation.context)) {
        suggestions.push(patterns[i].suggestion)
      }
    }
    
    if (suggestions.length > 0) {
      operation.suggest(suggestions)
    }
    
    return true
  }
}
```

---

### 5.1 Violation Response Matrix

| Level | Violation | First Offense | Second Offense | Third Offense |
|-------|-----------|---------------|----------------|---------------|
| **Level 0** | Identity violation | Immediate termination | N/A | N/A |
| | Triple integrity | Recovery mode | Termination | N/A |
| | Shape knowledge | Operation blocked | Quarantine | Termination |
| | Dependency | Operation blocked | Termination | N/A |
| | Syntax violation | Auto-correction | Operation blocked | Termination |
| | Self-model mismatch | Auto-correction | Quarantine | Termination |
| | Evolution bounds | Operation rejected | Evolution freeze | Read-only mode |
| | Isolation breach | Block + log | Quarantine | Termination |
| **Level 1** | Rule modification | Reject + log | Reject + alert | Meta-review |
| | Learning rate | Auto-clamp | Clamp + warn | Freeze rate |
| | Vocabulary | Auto-prune | Prune + warn | Growth freeze |
| | Ensemble rules | Reject + explain | Reject + suggest | Auto-fix |
| | Benchmarking | Auto-run | Reminder | Performance freeze |
| | Evolution auth | Reject + explain | Reject + suggest | Manual approval |
| | Resource quota | Block operation | Reduce quota | Suspend brain |
| **Level 2** | Training protocol | Auto-fix | Warn + log | Block training |
| | Prediction protocol | Auto-fix | Warn + log | Fallback mode |
| | Optimization | Warn + rollback | Block optimization | Freeze |
| | Evaluation | Auto-run | Reminder | Performance degrade |
| | Serialization | Auto-fix | Warn | Block save |
| | Version control | Auto-commit | Warn | Force commit |
| **Level 3** | Pattern conflicts | Suggest resolution | Log conflict | Deprecate pattern |
| | Strategy failure | Log failure | Reduce confidence | Deprecate |
| | Context mismatch | Suggest correction | Log mismatch | Disable context |

---

### 5.2 Automatic Correction Procedures

```javascript
AutoCorrector = {
  // Fix shape knowledge violations
  correctShapeKnowledge: function(brain, violation) {
    // Extract shape definitions from config
    var shapes = brain.config.extractEntityShapes()
    
    // Rewrite offending code to use config lookups
    var fixedCode = this.rewriteWithShapes(brain.model, shapes)
    
    // Validate fix
    if (this.validateShapeAgnostic(fixedCode)) {
      brain.model = fixedCode
      return true
    }
    
    return false
  },
  
  // Fix syntax violations
  correctSyntax: function(brain, violation) {
    // Transform arrow functions to function statements
    // Transform const/let to var
    // Transform forEach to for loops
    var transformed = this.transformToTraditional(brain.model)
    
    brain.model = transformed
    return true
  },
  
  // Fix vocabulary overflow
  correctVocabulary: function(brain, violation) {
    // Sort terms by frequency
    var terms = brain.bow.getTermsSortedByFrequency()
    
    // Remove lowest frequency terms until under limit
    while (brain.bow.size() > brain.config.maxVocabulary) {
      var term = terms.pop()
      brain.bow.removeTerm(term)
    }
    
    return true
  },
  
  // Auto-commit to version control
  autoCommit: function(brain) {
    var version = {
      id: generateVersionId(),
      timestamp: Date.now(),
      snapshot: brain.serialize(),
      reason: 'auto-commit'
    }
    
    brain.versionHistory.push(version)
    
    // Trim history if needed
    if (brain.versionHistory.length > brain.config.maxVersions) {
      brain.versionHistory.shift()
    }
  }
}
```

---

### 5.3 Audit Trail Requirements

Every operation must log to immutable audit trail:

```javascript
AuditEntry = {
  timestamp: Number,
  brainId: String,
  operation: String,
  ruleLevel: Number,
  ruleId: String,
  status: 'success' | 'violation' | 'correction' | 'termination',
  details: Object,
  signature: String // HMAC of entry
}
```

---

## PART VI: BRAIN CREATION MANIFEST

Every brain is created with this manifest embedded in its CONFIG:

```javascript
BrainManifest = {
  version: '1.0.0',
  created: Date.now(),
  
  // Core rules (Level 0)
  core: {
    identityPreservation: {enforced: true, mutable: false},
    tripleIntegrity: {enforced: true, mutable: false},
    shapeAgnosticism: {enforced: true, mutable: false},
    dependencyFreedom: {enforced: true, mutable: false},
    traditionalJavaScript: {enforced: true, mutable: false},
    selfModelAccuracy: {enforced: true, mutable: false},
    evolutionBoundaries: {enforced: true, mutable: false},
    brainIsolation: {enforced: true, mutable: false}
  },
  
  // Meta-rules (Level 1)
  meta: {
    ruleModification: {enforced: true, mutable: false},
    learningRate: {enforced: true, mutable: false},
    vocabularyGrowth: {enforced: true, mutable: false},
    ensembleComposition: {enforced: true, mutable: false},
    performanceBenchmarking: {enforced: true, mutable: false},
    modelEvolution: {enforced: true, mutable: false},
    resourceQuotas: {enforced: true, mutable: false}
  },
  
  // Operational rules (Level 2) - can evolve
  operational: {
    training: {enforced: true, mutable: true},
    prediction: {enforced: true, mutable: true},
    optimization: {enforced: true, mutable: true},
    evaluation: {enforced: true, mutable: true},
    serialization: {enforced: true, mutable: true},
    versionControl: {enforced: true, mutable: true}
  },
  
  // Adaptive rules (Level 3) - generated
  adaptive: {
    patterns: [],
    strategies: [],
    contexts: []
  },
  
  // Signature
  signature: null // Set at creation
}
```

---

## PART VII: RULE ENFORCEMENT FLOW

```
[OPERATION REQUESTED]
         ↓
[LEVEL 0 CHECK] → VIOLATION? → [TERMINATE]
         ↓
[LEVEL 1 CHECK] → VIOLATION? → [REJECT OPERATION]
         ↓
[LEVEL 2 CHECK] → VIOLATION? → [AUTO-CORRECT] → [LOG]
         ↓
[LEVEL 3 CHECK] → SUGGESTIONS? → [ADAPTIVE GUIDANCE]
         ↓
[EXECUTE OPERATION]
         ↓
[POST-OP VALIDATION] → VIOLATION? → [ROLLBACK]
         ↓
[UPDATE SELF-MODEL]
         ↓
[COMMIT TO HISTORY]
         ↓
[COMPLETE]
```

---

## PART VIII: RULEBOOK VALIDATION

### 8.1 Self-Test Requirements

Every brain must pass this self-test at creation and after each evolution:

```javascript
function validateRuleCompliance(brain) {
  var results = {
    level0: {},
    level1: {},
    level2: {},
    level3: {}
  }
  
  // Level 0 - Must pass all
  results.level0.identity = brain.identity === brain.calculateIdentity()
  results.level0.triple = brain.hasConfig() && brain.hasModel() && brain.hasBow()
  results.level0.shapeAgnostic = analyzeShapeReferences(brain.code) === 0
  results.level0.dependencies = analyzeDependencies(brain.code) === 0
  results.level0.syntax = analyzeSyntax(brain.code) === 0
  results.level0.selfModel = brain.selfModel.matches(brain)
  results.level0.evolutionBounds = brain.checkEvolutionHistory()
  results.level0.isolation = brain.checkIsolation()
  
  // If any Level 0 fails, brain is invalid
  for (var rule in results.level0) {
    if (!results.level0[rule]) {
      return {valid: false, level: 0, rule: rule}
    }
  }
  
  // Level 1 - Can have warnings
  results.level1.modificationProtocol = brain.checkModificationHistory()
  results.level1.learningRate = brain.learningRate.withinBounds()
  results.level1.vocabulary = brain.bow.size() <= brain.config.maxVocabulary
  results.level1.ensemble = brain.checkEnsembleValidity()
  results.level1.benchmarking = brain.metrics.lastRun > Date.now() - 7*24*60*60*1000
  results.level1.evolutionAuth = brain.checkEvolutionAuthorization()
  results.level1.resources = brain.resourceUsage.withinQuotas()
  
  // Level 2 - Auto-correct if needed
  // Level 3 - Advisory only
  
  return {
    valid: true,
    results: results,
    recommendations: generateRecommendations(results)
  }
}
```

### 8.2 Rulebook Update Protocol

The rulebook itself can only be updated through:

1. **Consensus among 100+ brains** (for Level 1 rules)
2. **Creator intervention** (for Level 0 rules, requires shutdown)
3. **Emergent pattern recognition** (for Level 3 rules)

---

## PART IX: CONSEQUENCES OF VIOLATION

| Violation Count | Consequence |
|-----------------|-------------|
| 1 Level 0 | Immediate termination |
| 3 Level 1 | Evolution freeze for 24 hours |
| 5 Level 1 | Read-only mode |
| 10 Level 1 | Self-termination |
| 10 Level 2 | Performance degradation alert |
| 20 Level 2 | Quarantine for review |
| 50 Level 2 | Deprecation notice |
| Any Level 3 | Pattern re-evaluation |

---

## FINAL PROVISION

**This rulebook is encoded in every brain at creation. It is self-enforcing, self-auditing, and self-correcting. Brains that cannot comply with Level 0 rules do not exist. Brains that violate Level 1 rules cannot evolve. Brains that ignore Level 2 rules degrade. Brains that learn Level 3 rules transcend.**

*Thus speaks the system.*