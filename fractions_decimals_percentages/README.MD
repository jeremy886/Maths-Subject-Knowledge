Equivalent fractions: proportional reasoning

```
import arcade as ac


def outline(left, right, top, bottom, denominator, line_width=1, line_color=ac.color.BLACK):
    # assert (top - bottom) % denominator == 0, "Please choose a correct denominator!"
    dy = (top - bottom) // denominator

    ac.draw_line(left, bottom, left, top, line_color, line_width)
    ac.draw_line(right, bottom, right, top, line_color, line_width)

    for cut in range(0, denominator):
        ac.draw_line(left, cut*dy, right, cut*dy, line_color, line_width)
        print("outline", right, cut*dy, left, cut*dy)


def fill_numerator(left, right, top, bottom, denominator, numerator, outline_width=1, fill_color=ac.color.CLASSIC_ROSE):

    # assert (top - bottom) % denominator == 0, "Please choose a correct denominator!"
    assert numerator <= denominator, "The numerator needs to be equal or smaller than the denominator!"
    dy = (top - bottom) // denominator
    offset = outline_width

    for cut in range(0, denominator):
        if cut < numerator:
            ac.draw_lrtb_rectangle_filled(left+offset, right-offset, (cut+1)*dy-offset, cut*dy+offset, fill_color)
        else:
            ac.draw_lrtb_rectangle_filled(left + offset, right - offset, (cut + 1) * dy - offset, cut * dy + offset,
                                          ac.color.BITTER_LEMON)
        print("fill", left+offset, right-offset, (cut+1)*dy-offset, cut*dy+offset)

    ac.draw_text(f"{numerator}/{denominator}", right + 10, bottom+10, ac.color.BLACK)

ac.open_window(1000, 600, "Equivalent Fractions")

ac.set_background_color(ac.color.BLEU_DE_FRANCE)
ac.start_render()

# ac.draw_lrtb_rectangle_filled(0, 100, 1000, 0, ac.csscolor.BLUE_VIOLET)
numerator, denominator = 3, 5
outline(0, 100, 600, 0, denominator, 2)
fill_numerator(0, 100, 600, 0, denominator, numerator, 2)

numerator, denominator = 6, 10
outline(200, 300, 600, 0, denominator, 2)
fill_numerator(200, 300, 600, 0, denominator, numerator, 2)

numerator, denominator = 12, 20
outline(400, 500, 600, 0, denominator, 2)
fill_numerator(400, 500, 600, 0, denominator, numerator, 2)

numerator, denominator = 18, 30
outline(600, 700, 600, 0, denominator, 2)
fill_numerator(600, 700, 600, 0, denominator, numerator, 2)

numerator, denominator = 36, 60
outline(800, 900, 600, 0, denominator, 2)
fill_numerator(800, 900, 600, 0, denominator, numerator, 2)

ac.finish_render()
ac.run()
```


![Equivalnt Fractions](https://github.com/jeremy886/Maths-Subject-Knowledge/blob/master/fractions_decimals_percentages/equivalent%20Fractions%203%20over%205.png)
