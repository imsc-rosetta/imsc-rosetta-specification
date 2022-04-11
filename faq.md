# General XML

## Note the use of xml:space="preserve"

This is essential because to represent existing formats well, we MUST preserve spaces in the subtitle.  Hence ALL whitespace inside every div is intended for display.

examples:

```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="dp_al_start"><p style="p_font2"><span>two lines</span></p><p style="p_font2"><span>left bottom</span></p></div>
```

vs
```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="dp_al_start">
  <p style="p_font2">
    <span>two lines</span>
  </p>
  <p style="p_font2">
    <span>left bottom</span>
  </p>
</div>
```

![](./test.svg)
