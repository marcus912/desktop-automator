# Desktop Automator

A Python-based desktop automation toolkit for simulating user interactions, automating repetitive tasks, and creating custom workflows using PyAutoGUI.

## 📋 Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage Examples](#usage-examples)
- [Configuration](#configuration)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)
- [Disclaimer](#disclaimer)

## ✨ Features

- **Mouse Automation**: Programmable mouse movements, clicks, and drag operations
- **Keyboard Simulation**: Type text, press keys, and execute hotkey combinations
- **Screen Interaction**: Capture screenshots and locate images on screen
- **Custom Workflows**: Chain multiple actions to create complex automation sequences
- **Cross-Platform**: Works on Windows, macOS, and Linux
- **Safety Features**: Built-in failsafe mechanisms to prevent runaway scripts
- **Configurable Delays**: Customizable timing between actions
- **Logging Support**: Comprehensive logging for debugging and monitoring

## 🚀 Installation

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Install from PyPI (Coming Soon)

```bash
pip install desktop-automator
```

### Install from Source

```bash
# Clone the repository
git clone https://github.com/yourusername/desktop-automator.git
cd desktop-automator

# Install dependencies
pip install -r requirements.txt

# Install the package
pip install -e .
```

### Dependencies

```bash
pip install pyautogui pillow opencv-python-headless numpy
```

## 🎯 Quick Start

```python
from desktop_automator import Automator

# Initialize the automator
auto = Automator()

# Move mouse to coordinates
auto.move_to(100, 200)

# Click at current position
auto.click()

# Type some text
auto.type_text("Hello, World!")

# Take a screenshot
auto.screenshot("screen.png")
```

## 📖 Usage Examples

### Basic Mouse Operations

```python
from desktop_automator import Automator

auto = Automator()

# Move mouse to specific position
auto.move_to(500, 300, duration=1.0)

# Click operations
auto.click()  # Single click
auto.double_click()  # Double click
auto.right_click()  # Right click

# Drag operations
auto.drag_to(700, 400, duration=2.0)
```

### Keyboard Automation

```python
# Type text with natural typing speed
auto.type_text("Automating desktop tasks", interval=0.1)

# Press single keys
auto.press_key('enter')
auto.press_key('tab')

# Hotkey combinations
auto.hotkey('ctrl', 'c')  # Copy
auto.hotkey('alt', 'tab')  # Switch windows
```

### Creating Custom Workflows

```python
from desktop_automator import Workflow

# Create a workflow
workflow = Workflow("Daily Tasks")

# Add actions to the workflow
workflow.add_action('move', x=100, y=100)
workflow.add_action('click')
workflow.add_action('wait', seconds=2)
workflow.add_action('type', text="Automated workflow")
workflow.add_action('press', key='enter')

# Execute the workflow
workflow.run()
```

### Image Recognition

```python
# Find and click on an image
button_location = auto.locate_on_screen('button.png')
if button_location:
    auto.click_on_image('button.png')

# Wait for an image to appear
auto.wait_for_image('loading_complete.png', timeout=30)
```

## ⚙️ Configuration

Create a `config.yaml` file to customize behavior:

```yaml
# config.yaml
automator:
  failsafe: true  # Move mouse to corner to abort
  failsafe_corner: "top-left"
  default_duration: 0.5  # Default movement duration
  typing_interval: 0.05  # Delay between keystrokes
  screenshot_region: null  # null for full screen
  
logging:
  level: "INFO"
  file: "automation.log"
  format: "%(asctime)s - %(levelname)s - %(message)s"

safety:
  max_retries: 3
  retry_delay: 1.0
  pause_between_actions: 0.1
```

## 📚 API Reference

### Automator Class

#### Methods

- `move_to(x, y, duration=0.5)`: Move mouse to coordinates
- `click(button='left', clicks=1)`: Perform mouse click
- `type_text(text, interval=0.0)`: Type text string
- `press_key(key)`: Press a single key
- `hotkey(*keys)`: Press key combination
- `screenshot(filename=None, region=None)`: Capture screenshot
- `locate_on_screen(image, confidence=0.8)`: Find image on screen

### Workflow Class

#### Methods

- `add_action(action_type, **kwargs)`: Add action to workflow
- `run()`: Execute all actions in sequence
- `save(filename)`: Save workflow to file
- `load(filename)`: Load workflow from file

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Setup

```bash
# Install development dependencies
pip install -r requirements-dev.txt

# Run tests
pytest tests/

# Run linting
flake8 desktop_automator/

# Format code
black desktop_automator/
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

This tool is designed for legitimate automation purposes such as:
- Automating repetitive tasks
- GUI testing and quality assurance
- Accessibility assistance
- Educational demonstrations

Please ensure you comply with all applicable laws, regulations, and terms of service when using this tool. The authors are not responsible for any misuse or damage caused by this software.

## 🐛 Troubleshooting

### Common Issues

**Issue**: PyAutoGUI fails to import on Linux
```bash
# Install required system packages
sudo apt-get install python3-tk python3-dev
```

**Issue**: Screenshots not working on macOS
```bash
# Grant screen recording permissions to Terminal/IDE
# System Preferences > Security & Privacy > Screen Recording
```

**Issue**: Failsafe not working
```python
# Ensure failsafe is enabled
import pyautogui
pyautogui.FAILSAFE = True
```


**Note**: Always use automation responsibly and in accordance with relevant policies and agreements.