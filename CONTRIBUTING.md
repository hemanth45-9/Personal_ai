# Contributing to Personal AI Agent

Thank you for your interest in contributing! Here's how to get started.

## Development Setup

```bash
# Clone the repository
git clone https://github.com/hemanth45-9/Personal_ai.git
cd Personal_ai

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Install development dependencies
pip install black pylint pytest pytest-cov
```

## Making Changes

1. Create a new branch for your feature: `git checkout -b feature/your-feature`
2. Make your changes
3. Format code: `make format`
4. Run linter: `make lint`
5. Run tests: `make test`
6. Commit with clear messages: `git commit -m "Add description of changes"`
7. Push to branch: `git push origin feature/your-feature`
8. Open a Pull Request

## Adding New Tools

1. Create a new class in `agent/tools.py` that inherits from `BaseTool`
2. Implement the `execute()` method
3. Register the tool in `agent/core.py` `_initialize_tools()`
4. Add tests in `tests/test_agent.py`
5. Update the README with tool description

Example:

```python
class MyNewTool(BaseTool):
    """Description of what the tool does"""
    
    def __init__(self):
        super().__init__(
            "my_tool",
            "Clear description for the LLM"
        )
    
    async def execute(self, **kwargs) -> Dict[str, Any]:
        """Implement your tool logic here"""
        try:
            # Your implementation
            return {"success": True, "result": "output"}
        except Exception as e:
            return {"success": False, "error": str(e)}
```

## Code Style

- Use PEP 8 style guide
- Format with `black`
- Use type hints
- Add docstrings to all functions and classes
- Write descriptive commit messages

## Testing

- Write tests for new features
- Run `make test` before submitting PR
- Aim for >80% code coverage

## Reporting Issues

- Use GitHub Issues for bug reports
- Include:
  - Clear description
  - Steps to reproduce
  - Expected vs actual behavior
  - Python version and OS
  - Full traceback if applicable

## Questions?

Open an issue or discussion on GitHub!
