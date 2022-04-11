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

<code><div style="display :flex; justify-content : center; align-items : center; height : 450px ; width: 800px; overflow: hidden" id="render-div"><div style="position: relative; width: 800px; height: 450px; margin: auto; inset: 0px; z-index: 0;"><div lang="el-GR" style="position: absolute; margin: 0px; display: flex; flex-direction: column; justify-content: flex-end; height: 360px; width: 640px; opacity: 1; top: 45px; left: 80px; overflow: hidden; padding: 0px; visibility: visible; writing-mode: horizontal-tb; z-index: auto;"><div style="margin: 0px; visibility: visible;"><div style="margin: 0px; visibility: visible;"><p style="margin: 0px; direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; line-height: 29.9981px; text-align: center; unicode-bidi: normal; visibility: visible; padding-left: 7px; padding-right: 7px;"><span style="margin: 0px; color: rgb(255, 255, 255); direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; text-decoration: none; text-combine-upright: none; unicode-bidi: normal; visibility: visible; white-space: pre-wrap;"><span style="padding-top: 1px; padding-bottom: 1.14286px;">
</span><span style="margin-left: -7px; padding-left: 7px; padding-top: 1.99109px; padding-bottom: 1.15177px;">  </span></span><span style="margin: 0px; color: rgb(255, 255, 255); direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; text-decoration: none; text-combine-upright: none; unicode-bidi: normal; visibility: visible; white-space: pre-wrap;"><span style="margin-right: -7px; padding-right: 7px; padding-top: 1.99109px; padding-bottom: 1.15177px;">two line </span></span><span style="margin: 0px; color: rgb(255, 255, 255); direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; text-decoration: none; text-combine-upright: none; unicode-bidi: normal; visibility: visible; white-space: pre-wrap;"><span style="padding-top: 1.99109px; padding-bottom: 1.15177px;">
</span><span style="margin-left: -7px; padding: 1.98218px 7px 2.16068px; margin-right: -7px;"> </span></span></p><p style="margin: 0px; direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; line-height: 29.9981px; text-align: center; unicode-bidi: normal; visibility: visible; padding-left: 7px; padding-right: 7px;"><span style="margin: 0px; color: rgb(255, 255, 255); direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; text-decoration: none; text-combine-upright: none; unicode-bidi: normal; visibility: visible; white-space: pre-wrap;"><span style="padding-top: 1px; padding-bottom: 1.14286px;">
</span><span style="margin-left: -7px; padding-left: 7px; padding-top: 1.99109px; padding-bottom: 1.15177px;">  </span></span><span style="margin: 0px; color: rgb(255, 255, 255); direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; text-decoration: none; text-combine-upright: none; unicode-bidi: normal; visibility: visible; white-space: pre-wrap;"><span style="margin-right: -7px; padding-right: 7px; padding-top: 1.99109px; padding-bottom: 1.15177px;">center bottom</span></span><span style="margin: 0px; color: rgb(255, 255, 255); direction: ltr; font-family: Arial, Helvetica, &quot;Liberation Sans&quot;, sans-serif; font-size: 23.9985px; font-style: normal; font-weight: normal; text-decoration: none; text-combine-upright: none; unicode-bidi: normal; visibility: visible; white-space: pre-wrap;"><span style="padding-top: 1.99109px; padding-bottom: 1.15177px;">
</span><span style="margin-left: -7px; padding: 1.98218px 7px 2.16068px; margin-right: -7px;"> </span></span></p></div></div></div></div></div></code>

