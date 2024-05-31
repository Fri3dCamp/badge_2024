# LVGL
badge_2024_micropython is build with LVLG v9.1 included

## links
- lvgl homepage https://lvgl.io/
- lvgl documentation https://docs.lvgl.io/9.1/

### python examples (v8.4)
unfortunately for v9.x the python examples are not available any more  
there are some differences between v8.x and v9.x https://docs.lvgl.io/9.0/CHANGELOG.html
- lvgl live python examples (v8.4) https://docs.lvgl.io/8.4/examples.html
- lvgl python examples source code (v8.4) (search for *.py files) https://github.com/lvgl/lvgl/tree/v8.4.0/examples

## online simulator
there is an online micropython + lvgl (v9.0) simulator available
https://sim.lvgl.io/v9.0/micropython/ports/webassembly/index.html


## Simulator Examples

### button
```python
# Initialize
import display_driver
import lvgl as lv
disp = lv.display_get_default()
disp.set_resolution(296,240)

# Create a button with a label
scr = lv.obj()

btn = lv.button(scr)
btn.align(lv.ALIGN.CENTER, 0, 0)
label = lv.label(btn)
label.set_text('Hello World!')

lv.screen_load(scr)
```

### canvas
```python
# Initialize
import display_driver
import lvgl as lv
disp = lv.display_get_default()
disp.set_resolution(296,240)

scr = lv.obj()

buf = lv.draw_buf_create(50,50,lv.COLOR_FORMAT.RGB565, lv.STRIDE_AUTO)
canvas = lv.canvas(src)
canvas.set_draw_buf(buf)
canvas.fill_bg(lv.color_hex(0xF1C40F), lv.OPA.COVER)
canvas.center()

lv.screen_load(scr)
```