# python_calc

# step 1 create test.py
This file is used to test basic functionality.
```
import sys

from PyQt5.QtWidgets import QApplication
from PyQt5.QtWidgets import QLabel
from PyQt5.QtWidgets import QWidget

app = QApplication(sys.argv)

window = QWidget()
window.setWindowTitle('PyQt5 App')
window.setGeometry(100, 100, 280, 80)
window.move(600, 15)
helloMsg = QLabel('This is Test', parent=window)
helloMsg.move(60, 30)

window.show()

sys.exit(app.exec_())

```

# step 2 create view.py
This file is used to interect with end users.
```
from PyQt5.QtCore import Qt

from PyQt5.QtWidgets import QMainWindow
from PyQt5.QtWidgets import QWidget
from PyQt5.QtWidgets import QGridLayout
from PyQt5.QtWidgets import QLineEdit
from PyQt5.QtWidgets import QPushButton
from PyQt5.QtWidgets import QVBoxLayout

class GUI(QMainWindow):
    """PyCalc's View (GUI)."""
    def __init__(self):
        """View initializer."""
        super().__init__()

        # Set some main window's properties
        self.setWindowTitle('Calculator')
        self.setFixedSize(235, 235)

        # Set the central widget and the general layout
        self.generalLayout = QVBoxLayout()
        # Set the central widget
        self._centralWidget = QWidget(self)
        self.setCentralWidget(self._centralWidget)
        self._centralWidget.setLayout(self.generalLayout)

        # Create the display and the buttons
        self._createDisplayLED()
        self._createButtons()


def _createDisplayLED(self):
        """Create the display."""
       
        # Create the display widget
        self.display = QLineEdit()
        # Set some display's properties
        self.display.setFixedHeight(35)
        self.display.setAlignment(Qt.AlignRight)
        self.display.setReadOnly(True)
       
        # Add the display to the general layout
        self.generalLayout.addWidget(self.display)
def _createButtons(self):
        """Create the buttons."""
        self.buttons = {}
        buttonsLayout = QGridLayout()
        # Button text | position on the QGridLayout
        buttons = {'7': (0, 0),
                   '8': (0, 1),
                   '9': (0, 2),
                   '/': (0, 3),
                   'C': (0, 4),
                   '4': (1, 0),
                   '5': (1, 1),
                   '6': (1, 2),
                   '*': (1, 3),
                   '(': (1, 4),
                   '1': (2, 0),
                   '2': (2, 1),
                   '3': (2, 2),
                   '-': (2, 3),
                   ')': (2, 4),
                   '0': (3, 0),
                   '00': (3, 1),
                   '.': (3, 2),
                   '+': (3, 3),
                   '=': (3, 4),}
       # Create the buttons and add them to the grid layout
        for btnText, pos in buttons.items():
            self.buttons[btnText] = QPushButton(btnText)
            self.buttons[btnText].setFixedSize(40, 40)
            buttonsLayout.addWidget(self.buttons[btnText], pos[0], pos[1])
        # Add buttonsLayout to the general layout
        self.generalLayout.addLayout(buttonsLayout)          
def setDisplayText(self, text):
        """Set display's text."""
        self.display.setText(text)
        self.display.setFocus()

def getDisplayText(self):
        """Get display's text."""
        return self.display.text()
def clearDisplay(self):
        """Clear the display."""
        self.setDisplayText('')
```

# step 3 create main.py
This file is used to the view file.
```
import sys


from PyQt5.QtWidgets import QApplication
from view import GUI
from  model import evaluateExpression
from controller import Controller

# Client code
def main():
    """Main function."""
    # Create an instance of QApplication
    pycalc = QApplication(sys.argv)
    # Show the calculator's GUI
    view = GUI()
    view.show()

model = evaluateExpression
Controller(model=model, view=view)

sys.exit(pycalc.exec_())
if __name__ == '__main__':
    main()
```

# step 4 create model.py
This file handle the calculator's operation.
```
ERROR_MSG = 'ERROR'

# Create a Model to handle the calculator's operation
def evaluateExpression(expression):
    """Evaluate an expression."""
    try:
        result = str(eval(expression, {}, {}))
    except Exception:
        result = ERROR_MSG

    return result
```

# step 5 controller.py
This file act as an interface between model and view files to view the render the final output.
