# General XML

### Note the use of xml:space="preserve"

<details><summary>tt xml:space="preserve"</summary>

This is essential because to represent existing formats well, we MUST preserve spaces in the subtitle.  Hence ALL whitespace inside every div is intended for display.

It is irrelevant for the rest of the file, and hence we state it as an attribute of the tt element, and allow it to apply to the whole file.

examples:

In order to display well, a div cannot contain any space outside of span elements, e.g.:
```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="dp_al_start"><p style="p_font2"><span>two lines</span></p><p style="p_font2"><span>left bottom</span></p></div>
```

The below div will display with all the extra spacing and CRs disturbing the line positions:
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

Spacing before and after div elements should not compromise presentation.
</details>

### Namespaces
  
<details><summary>Use of namespace prefixes</summary>
    
Namespace prefix processing is a large and unneccessary overhead when using common simple XML parsers.  By enforcing namespace prefixes, and a fixed set of namespaces, we simplify the parsing significantly.
    
</details>
