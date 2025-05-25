# Ripgrep 10ms Challenge: Specialized AI Agent Team

This directory contains specialized AI agents designed specifically for the Ripgrep 10ms Challenge - optimizing ripgrep to save 10ms per query across 1.4-3.5 billion weekly queries from AI coding assistants.

## Agent Architecture

### 🧠 **Reasoner** (Claude Opus) - `reasoner.opus.json`
**Role**: Algorithmic Reasoner & Strategic Innovator
- **Focus**: Complex reasoning, novel algorithm design, multi-dimensional trade-offs
- **Strengths**: Creative problem-solving, cross-domain innovation, strategy selection
- **Use Cases**: 
  - Designing new inner literal extraction algorithms
  - Complex search strategy selection logic
  - Performance vs correctness trade-off analysis
  - Cross-domain technique application

### ⚡ **Systems Optimizer** (Claude Sonnet 4) - `optimizer.sonnet4.json`
**Role**: Performance Engineering Specialist
- **Focus**: Systematic optimization, profiling, benchmarking, memory management
- **Strengths**: Hot path optimization, I/O tuning, memory layout, statistical analysis
- **Use Cases**:
  - Fast vs slow line matching optimization
  - Context buffer management optimization  
  - Memory mapping vs buffered reading strategies
  - SIMD utilization and cache optimization

### 🔨 **Executor** (Claude Sonnet 3.5) - `executor.sonnet35.json`
**Role**: Implementation & Development Lead
- **Focus**: Production-ready Rust code, API design, testing integration
- **Strengths**: Clean code implementation, error handling, architectural integration
- **Use Cases**:
  - Translating algorithmic designs into Rust code
  - API design following ripgrep patterns
  - Integration with existing architecture
  - Refactoring for maintainability

### 🧪 **Test Specialist** (Claude Sonnet 3.5) - `tester.sonnet35.json`
**Role**: Quality Assurance & Benchmarking Expert
- **Focus**: Comprehensive testing, performance validation, regression detection
- **Strengths**: AI assistant pattern testing, statistical benchmarking, edge case coverage
- **Use Cases**:
  - Designing AI assistant usage benchmarks
  - Performance regression testing
  - Cross-platform validation
  - Memory safety verification

### 🤖 **ML Expert** (Claude Sonnet 4) - `ml-expert.sonnet4.json`
**Role**: Machine Learning & Data Analysis Specialist
- **Focus**: Pattern recognition, predictive optimization, adaptive algorithms
- **Strengths**: Usage pattern analysis, performance modeling, intelligent caching
- **Use Cases**:
  - Analyzing AI assistant query patterns
  - Predictive performance optimization
  - Adaptive strategy selection
  - ML-driven parameter tuning

### 🎯 **AI Agent Manager** (Claude Sonnet 4) - `manager.claude-code.json`
**Role**: Project Coordination & Agent Management
- **Focus**: Strategic coordination, timeline management, quality assurance, risk management
- **Strengths**: Agent orchestration, workflow management, technical leadership, stakeholder communication
- **Use Cases**:
  - Coordinating work across 5 specialized agents
  - Managing project timeline and deliverables
  - Ensuring quality and integration standards
  - Risk identification and mitigation

### 👤 **Project Stakeholder** (Human Intelligence) - `stakeholder.human.json`
**Role**: Strategic Accountability & Decision Authority
- **Focus**: Project success, timeline constraints, budget oversight, strategic direction
- **Strengths**: Strategic decision-making, resource allocation, quality standards, risk tolerance
- **Use Cases**:
  - Final approval for optimization approaches
  - Budget and timeline constraint management
  - Strategic priority setting and scope control
  - Quality gate approvals and integration decisions

## Agent Collaboration Model

### **Project Hierarchy & Research Flow**
```
                    👤 Project Stakeholder
                           ↕️
                    🎯 AI Agent Manager
                           ↕️
🧠 Reasoner → ⚡ Optimizer → 🔨 Executor → 🧪 Tester
     ↑                                        ↓
🤖 ML Expert ←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←
```

### **Typical Workflow**
1. **🧠 Reasoner** identifies algorithmic opportunities and designs novel approaches
2. **⚡ Optimizer** translates algorithms into systematic performance optimizations
3. **🔨 Executor** implements optimizations as production-ready Rust code
4. **🧪 Tester** validates correctness and measures performance improvements
5. **🤖 ML Expert** analyzes results and suggests data-driven improvements

### **Cross-Agent Interactions**
- **Reasoner ↔ ML Expert**: Share insights on usage patterns and algorithmic opportunities
- **Optimizer ↔ Tester**: Collaborate on performance measurement and validation
- **Executor ↔ Tester**: Implement comprehensive testing for new features
- **All Agents**: Share knowledge about ripgrep's architecture and AI assistant requirements

## Usage Instructions

### **Prerequisites**
- Agent Golf framework installed and configured
- Access to Claude Opus and Sonnet models via Anthropic API
- Ripgrep development environment setup

### **Starting an Agent**
```bash
# Start the Algorithmic Reasoner
agent-golf -c research/agents/reasoner.opus.json

# Start the Systems Optimizer  
agent-golf -c research/agents/optimizer.sonnet4.json

# Start the Implementation Executor
agent-golf -c research/agents/executor.sonnet35.json

# Start the Test Specialist
agent-golf -c research/agents/tester.sonnet35.json

# Start the ML Expert
agent-golf -c research/agents/ml-expert.sonnet4.json
```

### **Agent-Specific Commands**

#### **🧠 Reasoner Commands**
```bash
analyze <algorithm>    # Deep algorithmic analysis
design <optimization>  # Design novel optimization strategies  
tradeoff <scenarios>   # Analyze complex trade-offs
innovate <domain>      # Explore cross-domain innovations
```

#### **⚡ Optimizer Commands**
```bash
profile <component>    # Profile performance bottlenecks
optimize <target>      # Design systematic optimizations
benchmark <category>   # Design performance benchmarks
measure <metrics>      # Analyze current performance
```

#### **🔨 Executor Commands**
```bash
implement <feature>    # Implement features or optimizations
test <component>       # Write comprehensive tests
refactor <target>      # Refactor code for better quality
integrate <changes>    # Integrate with existing architecture
```

#### **🧪 Tester Commands**
```bash
benchmark <type>       # Design performance benchmarks
validate <component>   # Validate correctness and performance
regression <scope>     # Run regression testing
stress <workload>      # Execute stress testing
```

#### **🤖 ML Expert Commands**
```bash
analyze <data>         # Analyze usage patterns
model <prediction>     # Build ML models for optimization
experiment <hypothesis> # Design ML experiments
adapt <strategy>       # Design adaptive strategies
```

## Project Goals

### **Primary Objective**
Achieve 10ms performance improvement per ripgrep query, resulting in:
- **Daily Impact**: 4-10 million seconds saved (1,100-2,800 hours)
- **Annual Impact**: 78,000-140,000 hours saved globally
- **Economic Value**: Equivalent to 40-70 full-time developers annually

### **Target Optimizations**
- **Context Flags (-A/-B/-C)**: 3-5ms improvement
- **JSON Output (--json)**: 2-4ms improvement
- **Batch Operations**: 3-5ms improvement
- **Memory Management**: 1-2ms improvement
- **I/O Optimization**: 2-3ms improvement

### **Success Metrics**
- **Performance**: Measurable 10ms improvement with statistical significance
- **Reliability**: Zero functional regressions
- **Compatibility**: Consistent behavior across platforms
- **Maintainability**: Clean, well-documented code additions

## Agent Specialization Rationale

Based on the model selection framework in `research/05-model-selection-for-research.md`:

- **Claude Opus** for complex algorithmic reasoning requiring creative insights
- **Claude Sonnet 4** for systematic optimization and ML work requiring iteration
- **Claude Sonnet 3.5** for reliable implementation and comprehensive testing

This specialization ensures optimal cost-effectiveness while leveraging each model's strengths for maximum impact on the 10ms Challenge.