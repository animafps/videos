---
aliases: 
tags: 
---
# G%A Tracking
```python
from manim import *


class TrackingReactivity(Scene):
    def construct(self):
        numberplane = NumberPlane({"stroke_color": BLUE_D})
        circle = Circle(color=TEAL_D, fill_opacity=0.9,
                        radius=0.5).shift(LEFT * 4)
        circleOutline = Circle(color=GREY, radius=0.6).shift(LEFT * 4)

        self.play(
            Create(numberplane, run_time=3, lag_ratio=0.1),
        )
        self.play(
            DrawBorderThenFill(circle),
            FadeIn(circleOutline),
        )
        self.wait()
        self.play(
            circle.animate(rate_func=linear, run_time=1.5).shift(RIGHT * 8),
            circleOutline.animate(
                rate_func=linear, run_time=1.5).shift(RIGHT * 8),
        )
        self.play(
            circleOutline.animate(run_time=0.2).shift(RIGHT * 8 / 1.5 * 0.2),
            circle.animate(rate_func=linear, run_time=0.2).shift(
                LEFT * 8 / 1.5 * 0.2),
        )
        self.play(
            circle.animate(rate_func=linear, run_time=0.3).shift(
                LEFT * 8 / 1.5 * 0.3),
            circleOutline.animate(run_time=0.3)
            .move_to(circle)
            .shift(LEFT * 8 / 1.5 * 0.3),
        )
        self.play(
            circleOutline.animate(
                rate_func=linear, run_time=1).shift(LEFT * 8 / 1.5),
            circle.animate(rate_func=linear, run_time=1).shift(LEFT * 8 / 1.5),
        )
        self.wait()
```