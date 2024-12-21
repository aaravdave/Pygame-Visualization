# p3D
### A cross-platform, fully-featured 3D engine, made in Python.
## Getting Started
To install the package, run this command in the directory of your project's code.
```commandline
pip install python3D
```
You can now start writing your first 3D script. Paste the following code to get started.
```python
import python3D as p3D


def setup():
    """Put your setup code here, to run once."""
    global models


def loop(elapsed_time):
    """Put your main code here, to run repeatedly."""


p3D.run(setup, loop)
```
> The `setup` and `loop` functions are not required parameters of `p3D.run()`, but all project functions are added in them.

You're ready to start developing in 3D!

## Documentation
### Models
To add an OBJ model, you can use the `models` registry in your `setup()` function.
```python
def setup():
    """Put your setup code here, to run once."""
    global models
    models['model'] = p3D.Model('model.obj', 'optional_texture.png')
```
To modify the transformational properties of your models, you can use the `change_position()` property.
```python
models['model'].change_position(x=1)
```
> When in the `loop()` function, you must use `p3D.models['model']` instead.

`x`, `y`, `z` - left/right, up/down, and forward/backward displacements, respectively

`rot_x`, `rot_y`, `rot_z` - rotation on x, y, and z axes, respectively

`scale` - percentage-based size change of model. *Support for axis-based scaling is not supported at this time.*

`reset` - takes inputted values as the new position of the model when set to `1`; `0` by default (adds new values to current values).

### Preferences
`p3D.preferences` can be used to modify functionality by changing an attribute.
```python
p3D.preferences['attribute'] = value
```
The following attributes are available:
- `'title'` - string used for default loading screen, window caption, and system logs. `'p3D'` by default.
- `'camera'` - list `[x, y, z, h, v]` of starting camera attributes where `x`, `y`, `z` is the position of the camera and `h`, `v` is the starting horizontal and vertical camera angles. `[0, 0, 0, 0.01, 0.01]` by default.
  - The amount of decimal places in the starting horizontal and vertical camera angles is the amount of decimal places possible in simulation. For example, having `0`, `0` as your `h`, `v` values would make the camera rotate in integer values only, reducing freedom.
- `'font'` - string file path to font file of choice. `'font.ttf'` by default.
- `'skybox'` - string file path to skybox image of choice; replaces black environment. `None` by default.
- `'loading'` - function taking parameters `surface` and `title`, regardless of whether they are used. Custom loading screens must be drawn on with pygame functions.

### Logs
The `p3D.log()` function takes in three parameters (`prefix`, `message`, `data=None`) and logs in the command line in color, if supported.

`prefix` - determines type of message sent. Possible values include:
- `'warning'`: yellow, user warnings
- `'error'`: red, both computational and logical errors
- `'log'`: blue, general messages, runtime checkpoints, and data logging

`message` - message body to be sent; should be one line.

`data` - list, where each item appears after the message body on a separate line.

#### Proper Usage
When using the `p3D.log()` function, following proper usage guides can ensure that in-built engine logs match the style of your project's logs.
- Use warnings when something atypical for your project (e.g., a user hasn't claimed their account and information may be lost) occurs, **NOT** when an error is anticipated.
- Errors should be used for issues specific to your project (e.g., an item is too expensive for the player to buy).
  - If a runtime error occurs, `FATAL. ` must precede your `message`, and for specific errors, you must include relevant information (e.g. filenames) in the `data` list.
  - If the error is not specific (i.e. general `Exception`), then after relevant information, include `f'Error {str(e)}` in the `data` list.
  - Unhelpful error messages often don't include a fix or course of action.
- Make sure to log all important stages of app progression (e.g, a user signs up).

# Other
### Issue Reporting
To report issues, please refer to our [GitHub Issues](https://github.com/aaravdave/p3D/issues) page.
### Contacts
For questions concerning the contents of this repository, please contact aaravhdave [at] gmail [dot] com.
