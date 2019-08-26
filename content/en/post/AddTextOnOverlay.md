---
title: "Add Text On Ovitos Overlay"
date: 2019-08-25T18:39:00-04:00
draft: false
---

```Python
# This user-defined function is called by OVITO to let it draw arbitrary graphics on top of the viewport.
from PyQt5.QtGui import QPainter, QColor, QFont
def render(args):
    
    # This demo code prints the current animation frame into the upper left corner of the viewport.
    text1 = "{:.2f} ps".format(args.frame*0.2)
    font=args.painter.font()
    font.setPointSize(18)
    args.painter.setFont(font)
    args.painter.setPen(QColor(255, 255, 255))
    args.painter.drawText(280, 80 + args.painter.fontMetrics().ascent(), text1)
```
