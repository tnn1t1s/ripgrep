# Agent Results Documentation Structure

## Directory Structure

All agent results and outputs should be organized as follows:

```
research/agents/{agent_name}/results/{task_type}_{YYMMDD_HHMM}.md
```

## Components

### Agent Name
- `manager` - AI Agent Manager coordination and tracking
- `reasoner` - Algorithmic Reasoner analysis and insights  
- `optimizer` - Systems Optimizer performance work
- `executor` - Implementation Executor code changes
- `tester` - Test Specialist validation and benchmarks
- `ml-expert` - ML Expert pattern analysis and optimization

### Task Type
Descriptive category indicating the type of work performed:

**Analysis Tasks:**
- `baseline_performance` - Initial performance measurements
- `algorithm_analysis` - Deep dive into algorithmic behavior
- `memory_profiling` - Memory usage and allocation patterns
- `pattern_analysis` - Usage pattern identification

**Optimization Tasks:**
- `file_type_optimization` - File filtering improvements
- `context_window_optimization` - Context flag improvements
- `cache_optimization` - Caching strategy implementations
- `memory_optimization` - Memory usage improvements

**Implementation Tasks:**
- `feature_implementation` - New feature development
- `bug_fix` - Defect resolution
- `refactor` - Code structure improvements
- `integration` - Component integration work

**Validation Tasks:**
- `benchmark_results` - Performance benchmark data
- `regression_testing` - Validation that changes don't break existing functionality
- `correctness_validation` - Verification of output accuracy

### Date/Time Format
- `YYMMDD_HHMM` - Year, Month, Day, Hour, Minute
- Example: `250525_1420` = May 25, 2025 at 2:20 PM

## File Content Structure

Each result file should contain:

1. **Header** - Task type, date, environment details
2. **Executive Summary** - Key findings and outcomes
3. **Detailed Results** - Measurements, analysis, or implementation details
4. **Actionable Items** - Next steps for other agents
5. **Validation Commands** - Reproducible commands for verification
6. **Success Metrics** - How to measure if goals were achieved

## Examples

```
research/agents/tester/results/baseline_performance_250525_1420.md
research/agents/optimizer/results/file_type_optimization_250525_1500.md
research/agents/reasoner/results/algorithm_analysis_250525_1600.md
research/agents/executor/results/feature_implementation_250525_1700.md
```

## Benefits

- **Agent Accountability** - Clear ownership of all work
- **Chronological Tracking** - Easy to see progress and evolution
- **Task Categorization** - Organized by type of work performed
- **Conflict Prevention** - Multiple agents can work simultaneously
- **Reproducibility** - Commands and contexts preserved for validation
- **Knowledge Transfer** - Results easily referenced by other agents

## Usage Guidelines

1. **Create immediately** when completing any significant analysis or implementation
2. **Reference in handoffs** when passing work between agents  
3. **Update task lists** to point to result files for context
4. **Validate commands** ensure others can reproduce your work
5. **Cross-reference** link related results across agents when relevant