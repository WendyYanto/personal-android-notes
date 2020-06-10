# CSS Notes

## Flex

```css
.container {
  display: flex;
  display: inline-flex;
  flex-direction: row;            /* ltr - default */
  flex-direction: row-reverse;    /* rtl */
  flex-direction: column;         /* top-bottom */
  flex-direction: column-reverse; /* bottom-top */

  flex-wrap: nowrap; /* one-line */
  flex-wrap: wrap;   /* multi-line */

  align-items: flex-start; /* vertical-align to top */
  align-items: flex-end;   /* vertical-align to bottom */
  align-items: center;     /* vertical-align to center */
  align-items: stretch;    /* same height on all (default) */

  justify-content: flex-start; /* horizontal alignment - default */
  justify-content: flex-end;
  justify-content: center;
}
```

## References

1. <https://www.sketchingwithcss.com/samplechapter/cheatsheet.html>
