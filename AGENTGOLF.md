# Agent-Golf Power User Guide

Agent-golf is a framework for running specialized AI agents with custom tools and configurations. This guide covers advanced usage patterns, configuration strategies, and power user features.

## Core Concepts

### Agent Configuration Structure
```json
{
  "version": "1.0.0",
  "api": {
    "endpoint": "https://api.anthropic.com/v1/messages",
    "version": "2023-06-01",
    "max_tokens": 4096
  },
  "provider": "anthropic",
  "model": {
    "default": "claude-3-5-sonnet-20241022"
  },
  "tools": [...],
  "post_tool_prompt": ""  // New: Control continuation behavior
}
```

## Command Line Interface

### Essential Flags
```bash
# Basic execution
agent-golf --agent-config /absolute/path/to/config.json

# Oneshot mode (no conversation loop)
agent-golf --agent-config config.json --no-loop --prompt "Task description"

# Control continuation behavior
agent-golf --agent-config config.json --continue-prompt ""  // Clean stops
agent-golf --agent-config config.json --continue-prompt "Next step?" // Custom prompts

# Config validation
agent-golf --agent-config config.json --show  // Validate without running
```

### Path Handling
- **Always use absolute paths** for `--agent-config`
- Relative paths resolve from agent-golf installation directory
- Alternative: Copy configs to agent-golf's config/agents/ directory

## Advanced Configuration

### Model Selection Strategy
```json
{
  "model": {
    "default": "claude-3-5-sonnet-20241022",    // Fast, efficient
    "reasoning": "claude-3-opus-20240229",       // Deep analysis
    "systems": "claude-3-5-sonnet-20241022"     // Systems optimization
  }
}
```

### Tool Configuration Best Practices
```json
{
  "tools": [
    {
      "name": "bash",
      "description": "Execute bash commands with timeout and output capture",
      "enabled": true,
      "parameters": {
        "type": "object",
        "properties": {
          "command": {"type": "string"},
          "timeout": {"type": "number", "default": 120}
        },
        "required": ["command"]
      }
    }
  ]
}
```

### Continuation Control
```json
{
  "post_tool_prompt": "",                    // No forced continuation (recommended)
  "post_tool_prompt": "Continue analysis",   // Custom continuation
  "post_tool_prompt": "Take the next small step"  // Default behavior
}
```

## Specialized Agent Patterns

### Test Specialist Agent
```json
{
  "version": "1.0.0",
  "model": {"default": "claude-3-5-sonnet-20241022"},
  "tools": [
    {"name": "design_benchmark", "enabled": true},
    {"name": "validate_correctness", "enabled": true},
    {"name": "bash", "enabled": true}
  ],
  "post_tool_prompt": "",  // Let agent decide when complete
  "system_prompt": "You are a Test Specialist focused on performance benchmarking..."
}
```

### Systems Optimizer Agent  
```json
{
  "model": {"default": "claude-3-5-sonnet-20241022"},
  "tools": [
    {"name": "profile_performance", "enabled": true},
    {"name": "optimize_implementation", "enabled": true},
    {"name": "bash", "enabled": true}
  ],
  "post_tool_prompt": "Analyze next optimization opportunity"
}
```

## Error Handling & Debugging

### Tool Use Conversation State
**Fixed in latest version** - agent-golf now properly handles:
- Unmatched tool_use blocks
- Tool execution failures  
- Custom tool definitions
- Conversation state recovery

### Common Issues & Solutions
```bash
# Config not found - use absolute paths
agent-golf --agent-config /full/path/to/config.json

# Tool crashes - ensure tools are properly defined
agent-golf --agent-config config.json --show  # Validate first

# Infinite loops - disable continuation prompts
agent-golf --agent-config config.json --continue-prompt ""
```

## Multi-Agent Coordination Patterns

### Agent Specialization Strategy
1. **Manager Agent** - Coordinates other agents, tracks progress
2. **Reasoner Agent** - Deep algorithmic analysis (Claude Opus)
3. **Optimizer Agent** - Systems performance work (Claude Sonnet 4)
4. **Executor Agent** - Implementation work (Claude Sonnet 3.5)
5. **Tester Agent** - Validation and benchmarking (Claude Sonnet 3.5)
6. **ML Expert Agent** - Pattern analysis and ML optimization

### Communication Protocols
- **GitHub Issues** - Formal task assignment and handoffs
- **Result Files** - Structured outputs in `research/agents/{agent}/results/`
- **Status Updates** - Progress tracking via issue comments

## Performance Optimization

### Model Selection for Task Types
- **Complex Reasoning**: Claude Opus - slow but thorough
- **Systems Work**: Claude Sonnet 4 - balanced performance/capability  
- **Implementation**: Claude Sonnet 3.5 - fast, reliable coding
- **Analysis**: Claude Sonnet 3.5 - good balance for most tasks

### Oneshot vs Interactive
```bash
# Oneshot - better for focused tasks
agent-golf --no-loop --prompt "Specific task"

# Interactive - better for exploration
agent-golf  # Starts conversation loop
```

## Real-World Usage Examples

### Benchmark Analysis
```bash
agent-golf --agent-config /path/to/tester.json --no-loop --continue-prompt "" \
  --prompt "Analyze benchmark data in benchsuite/runs/ and identify performance patterns"
```

### Code Optimization
```bash
agent-golf --agent-config /path/to/optimizer.json \
  --prompt "Optimize file type filtering performance in crates/ignore/src/types.rs"
```

### Algorithm Analysis
```bash
agent-golf --agent-config /path/to/reasoner.json --no-loop \
  --prompt "Analyze why larger context windows perform better than smaller ones"
```

## Best Practices

1. **Use absolute paths** for all config references
2. **Validate configs** with `--show` before running
3. **Disable continuation prompts** for specialized agents (`--continue-prompt ""`)
4. **Test in oneshot mode** first (`--no-loop`)
5. **Structure results** systematically for agent coordination
6. **Choose appropriate models** based on task complexity
7. **Use custom tools** sparingly - bash covers most needs

## Recent Improvements (2025-05-25)

- ✅ **Tool use conversation state fix** - No more crashes on tool execution
- ✅ **Configurable continuation prompts** - Control agent completion behavior  
- ✅ **CLI continuation override** - Task-level prompt control
- ✅ **Robust error handling** - Graceful tool failure recovery
- ✅ **Custom tool support** - Clear error messages for undefined tools

## Future Development Areas

- **Agent-to-agent communication** - Direct handoffs without GitHub
- **Parallel agent execution** - Multiple agents on different tasks
- **Result aggregation** - Automated combination of agent outputs
- **Performance monitoring** - Agent execution time and token usage tracking