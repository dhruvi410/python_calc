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

# step 3 create main.py
This file is used to the view file.

# step 4 create model.py
This file handle the calculator's operation.

# step 5 controller.py
This file act as an interface between model and view files to view the render the final output.
