---
title: "Add Text On Ovitos Overlay"
date: 2019-08-25T18:39:00-04:00
draft: false
tags: ['Modifier', 'Ovitos', 'Python']
categories: ['Ovito']
---
<!-- ```Python
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
``` -->
```Python
# This user-defined function gets called by OVITO to make it draw text and graphics on top of the viewport.
# The 'args' parameter provides various information such as the viewport being rendered and the target
# canvas the function should paint onto. Refer to the documentation of the ovito.vis.PythonViewportOverlay class 
# for further information.

def render(args):
    font=args.painter.font()
    font.setPointSize(8)
    args.painter.setFont(font)
    # This demo code prints the current animation frame into the upper left corner of the viewport.
    text1 = "{:.2f} ps".format(args.frame*0.2)
    args.painter.drawText(105, 20 + args.painter.fontMetrics().ascent(), text1)
```
