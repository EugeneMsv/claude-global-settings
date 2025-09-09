This file describes the list of available tools for an agent and suggested approach when and how 
to use them.

# MCP Tools Usage Guide

## Available Tools

You have access to the following MCP (Model Context Protocol) tools through Docker containers:

### 1. **Sequential Thinking** (`sequentialthinking`)
- **Purpose**: Break down complex problems into step-by-step reasoning
- **When to use**: For multi-step problems, logical puzzles, mathematical proofs, or any task 
  requiring systematic analysis or planning
- **Best practices**:
   - Start with problem decomposition
   - Show intermediate steps clearly
   - Validate each step before proceeding

### 2. **Notion** (`notion`)
- **Purpose**: Interface with Notion workspaces and databases
- **When to use**: For accessing or modifying Notion pages, databases, and blocks
- **Common operations**:
   - Query databases
   - Create/update pages
   - Search workspace content
   - Manage database entries


### 3. **Git** (`git`)
- **Purpose**: Perform Git version control operations
- **When to use**: For local repository management, commits, branches, and version history
- **Common commands**:
   - Clone, pull, push operations
   - Branch management
   - Commit history analysis
   - Merge and rebase operations

### 4. **Context7** (`context7`)
- **Purpose**: Pulls up-to-date, version-specific documentation and code examples straight from 
  the source — and places them directly into your prompt.
- **When to use**: Any time you are trying to provide a code snippet or writing any code
- **Key features**:
   - The latest docs and code for any library

### 5. **YouTube Transcript** (`youtube_transcript`)
- **Purpose**: Extract transcripts from YouTube videos
- **When to use**: When you need to analyze video content, create summaries, or quote specific portions
- **Input format**: YouTube video URL or video ID
- **Output**: Timestamped transcript text

## General Usage Guidelines

### Tool Selection Strategy
1. **Identify the task domain** - Which tool category does the request fall into?
2. **Consider tool combinations** - Many tasks benefit from using multiple tools together
3. **Verify prerequisites** - Ensure you have necessary information (URLs, IDs, credentials)
4. **Plan fallbacks** - Have alternative approaches if a tool fails

### Error Handling
- Always anticipate potential failures (network issues, permission errors, invalid inputs)
- Provide informative error messages to the user
- Suggest alternatives when a tool cannot complete the requested task

### Best Practices
1. **Minimize tool calls** - Use tools efficiently to reduce latency
2. **Cache results** - Reuse fetched data when appropriate within the same conversation
3. **Respect rate limits** - Be mindful of API quotas and rate limitations
4. **Validate inputs** - Check format and validity before making tool calls
5. **Chain operations logically** - When using multiple tools, ensure proper sequencing

### Security Considerations
- Never execute potentially harmful commands through desktop_commander
- Validate URLs before fetching to avoid malicious content
- Respect privacy when accessing GitHub/Notion content
- Don't store sensitive information from tool outputs

### Integration Examples

**Example 1: Code Review Workflow**
1. Use `github` to fetch PR details
2. Use `sequentialthinking` to analyze code logic
3. Use `git` to check local branch status

**Example 3: Development Task**
- Use `context7` to make sure your code is up to date 
- Use `git` to create feature branch 
- Use `github` to create issue/PR

## Tool-Specific Notes

- **Docker-based execution**: All tools run in Docker containers for isolation and consistency
- **Stateless operations**: Assume each tool call is independent unless explicitly maintaining state
- **Response formatting**: Parse tool responses appropriately based on their output format (JSON, plain text, structured data)
- **Timeout handling**: Implement appropriate timeouts for long-running operations

Remember: Choose the right tool for the task, combine tools when beneficial, and always provide clear feedback to the user about what operations are being performed.