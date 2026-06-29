---
title-slide: false
bibliography: references.bib
csl: vancouver.csl
citeproc: true
theme: serif
background-color: "#ffffff"
transition: slide
navigationMode: linear
hash: true
---

:::: {.columns}
::: {.column width="50%"}

## Sample slides
#### PlaceHolderName
#### Universiti Malaysia Perlis
#### [placeholder@email.com](mailto:placeholder@email.com)

<audio id="bg-music" src="media/audio/sb.m4a" loop></audio>

<div id="audio-credit"
     style="position: absolute; bottom: 40px; right: 20px; font-size: 0.6em; opacity: 0.6;">
  Music: “Adrift” by Scott Buckley (CC BY 4.0)
</div>

<script>
  document.addEventListener('DOMContentLoaded', () => {
    const audio = document.getElementById('bg-music');
    const credit = document.getElementById('audio-credit');

    // hide credit by default
    credit.style.display = 'none';

    const test = new Audio('media/audio/bgm.mp3');

    test.addEventListener('canplaythrough', () => {
      // bgm.mp3 exists → use it, keep credit hidden
      audio.src = 'media/audio/bgm.mp3';
    }, { once: true });

    test.addEventListener('error', () => {
      // bgm.mp3 missing → sb.m4a will play → show credit
      credit.style.display = 'block';
    }, { once: true });

    document.addEventListener('click', () => {
      if (Reveal.getIndices().h === 0) {
        audio.volume = 0.5;
        audio.play();
      }
    }, { once: true });

    Reveal.on('slidechanged', (event) => {
      if (event.indexh > 0) { audio.pause(); }
      else { audio.play(); }
    });
  });
</script>

:::

::: {.column width="50%"}
![](media/pics/logo1.png)
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Slide one
**Key Concepts:**
- Energy conservation per @carnot1824.
- $\Delta U = Q - W$
:::

::: {.column width="50%"}
![](media/pics/sample.png)
:::
::::

---

<span class="slide-title" data-title="My Hidden Slide Name"></span>

![](media/pics/wide.jpeg)

---

:::: {.columns}
::: {.column width="50%"}
### The Master Equation
The fundamental relation of thermodynamics:

$$\Delta U = Q - W$$

The work done $W$ is positive when the system expands against an external pressure.
:::

::: {.column width="50%"}
<video data-src="media/videos/sample.mp4" data-autoplay loop muted width="100%"></video>
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Visualizing the Gas Law
**Interactive Model:**

- P, V, and T relationships.
- Use the slider to adjust pressure.
- Observe the phase boundary.
:::

::: {.column width="50%"}
<iframe 
  data-src="media/plots/sample.html" 
  width="100%" 
  height="500px" 
  style="border:none;" 
  scrolling="no">
</iframe>
:::
::::

---

:::: {.columns}
::: {.column width="50%"}
### Impact of Process Parameters on Part Resistance

To understand the effect of varying `Temperature` and `Pressure` on `PartResistance`, we performed an ANOVA analysis. The upper specification limit (USL) for `PartResistance` is 10, with no lower specification limit, implying that lower resistance values are generally desirable.

The ANOVA results (which you can find in the output of the R cell above) will indicate the statistical significance of `Temperature`, `Pressure`, and their interaction on `PartResistance`. The box plots below visually summarize the distribution of `PartResistance` across different combinations of these process parameters, helping to identify which settings might yield lower and more consistent resistance.

:::

::: {.column width="50%"}
<iframe data-src='media/plots/resistance_boxplot.html' width='100%' height='500px' style='border:none;'></iframe>
:::
::::


----

:::: {.columns}
::: {.column width="50%"}
### Impact of Process Parameters on Part Resistance (Machine 1)

To understand the effect of varying `Temperature` and `Pressure` on `PartResistance` for Machine 1, we performed an ANOVA analysis. The upper specification limit (USL) for `PartResistance` is 10, with no lower specification limit.

The ANOVA results indicate a highly statistically significant effect of both `Temperature` and `Pressure` on `PartResistance` (p-values < 2e-16). However, the interaction effect between `Temperature` and `Pressure` is not statistically significant (p-value = 0.704). This suggests that while temperature and pressure individually influence part resistance, their combined effect is not significantly different from the sum of their individual effects for Machine 1. The box plots on the right visually summarize the distribution of `PartResistance` across different combinations of these process parameters.

:::

::: {.column width="50%"}
<iframe data-src='media/plots/resistance_boxplot.html' width='100%' height='500px' style='border:none;'></iframe>
:::
::::


----

:::: {.columns}
::: {.column width="50%"}
### Process Parameters Influence on Part Resistance (Machine 1)

Further analysis on Machine 1 reveals how specific `Temperature` and `Pressure` settings affect `PartResistance`. The ANOVA results previously indicated that both parameters significantly influence part resistance, while their interaction was not significant. 

This boxplot visualization demonstrates the distribution of `PartResistance` for different combinations of `Temperature` and `Pressure` for Machine 1. It allows us to visually confirm that certain temperature and pressure combinations tend to yield lower and more consistent `PartResistance` values, which is desirable given the upper specification limit (USL) of 10.

Experimenting with these parameters is crucial for optimizing the manufacturing process to minimize defects.

:::

::: {.column width="50%"}
<iframe data-src='media/plots/machine1_resistance_boxplot.html' width='100%' height='500px' style='border:none;'></iframe>
:::
::::

---
# Bibliography
<div id="refs"></div>
