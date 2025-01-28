# Code Analysis Tool

A tool for analyzing code projects, monitoring file changes, and generating comprehensive reports to give context for language models prompts. This tool is designed to help developers understand their projects better by providing insights into code structure and tracking changes over time.

## Features

- **Token-Aware Analysis**: Intelligently analyzes your codebase while respecting token limits
- **Real-Time Monitoring**: Watches for file changes and automatically generates updated reports
- **Smart File Selection**: Prioritizes recently modified files
- **Directory Filtering**: Optionally focus analysis on specific directories and their subdirectories
- **Custom File Extensions**: Support for any programming language through configurable file extensions
- **Comprehensive Reporting**: Generates detailed reports including:
  - Project structure overview
  - File contents with syntax highlighting
  - Token usage statistics
  - Recent modifications tracking

## Installation

```bash
# Clone the repository
git clone [your-repo-url]
cd [repo-name]

# Install required dependencies
pip install watchdog
```

## Usage

The tool consists of two main components:

### 1. Code Analyzer (code_analyzer.py)

Run a one-time analysis of your project:

```bash
python code_analyzer.py --dir ./your_project --report --include src tests --extensions .py .js .ts
```

Options:
- `--dir`, `-d`: Specify the directory to analyze
- `--report`, `-r`: Generate a complete project report
- `--include`, `-i`: List of specific directories to include in the analysis
- `--extensions`, `-e`: List of file extensions to analyze (e.g., .py .js .cpp)

### 2. File Watcher (watch_analyzer.py)

Monitor your project for changes and automatically generate updated reports:

```bash
python watch_analyzer.py --dir ./ --include src tests --extensions .py .js .ts
```

Options:
- `--dir`, `-d`: Directory to monitor (default: current directory)
- `--cooldown`, `-c`: Minimum time between analyses in seconds (default: 5)
- `--include`, `-i`: List of specific directories to monitor
- `--extensions`, `-e`: List of file extensions to monitor

The watcher will:
- Monitor specified file types
- Generate an initial report
- Create new reports when changes are detected (with a configurable cooldown period)
- Focus monitoring on specified directories if provided

## Configuration

The tool comes with sensible defaults but can be customized:

- **Token Limits**: Adjust `MAX_TOKENS` and `CHARS_PER_TOKEN` in `CodeAnalyzer`
- **Excluded Directories**: Modify `EXCLUDED_DIRECTORIES` to skip specific folders
- **Default Extensions**: Update `INCLUDED_EXTENSIONS` to change default file types
- **Cooldown Period**: Adjust the minimum time between analyses in `CodeWatcher`
- **Included Directories**: Specify directories to focus the analysis on

## Output

Reports are generated in the `code_analysis` directory and include:
- Overall project statistics
- List of monitored directories and file extensions
- File contents with metadata
- List of excluded files
- Token usage statistics

## How It Works

1. **File Discovery**: The tool scans your project, identifying relevant files while respecting exclusion patterns and directory filters.

2. **Smart Selection**: Files are prioritized based on:
   - Recent modifications
   - File size
   - Token budget constraints
   - Directory inclusion rules

3. **Report Generation**: Comprehensive reports are created, combining structural analysis with content preservation.

4. **Real-Time Monitoring**: The watcher component tracks file changes and triggers new analyses when needed.

## Default Supported File Extensions

The tool supports a wide range of programming languages by default:
- `.py` (Python)
- `.js` (JavaScript)
- `.java` (Java)
- `.cpp`, `.c`, `.h`, `.hpp` (C/C++)
- `.cs` (C#)
- `.php` (PHP)
- `.rb` (Ruby)
- `.go` (Go)
- `.rs` (Rust)
- `.ts` (TypeScript)
- `.html` (HTML)
- `.css`, `.scss`, `.sass`, `.less` (CSS and preprocessors)

Additional extensions can be added using the `--extensions` parameter.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Authors

Giuseppe Birardi
