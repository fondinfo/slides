![](http://fondinfo.github.io/images/repr/binary-hacker.jpg)
# Multimedia
## Introduction to Computer Science <br> Michele Tomaiuolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/repr/guybrush.png)
# Images

---

![](http://fondinfo.github.io/images/repr/rgb-raster.png)
# ⭐ Raster Images

- *Digitalization*: from image to binary sequence
- **Raster image**: divided into a grid of points
    - Each point (**pixel**) described by a code
    - The code identifies the color
- **Depth**: # bits assigned to each pixel
    - To represent its color
    - 1, 2, 8, 12, 16, 24, 32… bits per pixel (*bpp*)
    - E.g. 8 bits for `$256 (=2^8)$` possible colors
    - Direct color or indexed by a **palette**
- **Resolution**: # points per inch (*dpi*), as in typography
    - Often (but not always), horizontal resolution equals vertical

---

![](http://fondinfo.github.io/images/repr/spectral-sensitivity.svg) ![](http://fondinfo.github.io/images/repr/additive-color.svg) Red, green, blue + <br> Cyan, magenta, yellow
# 🔬 Color Models

- Eye sensitive to brightness variations
    - 6 million cones, 125 million rods
- **RGB**: red, green, blue
    - 8 bits: 3 bits × R and G, 2 × B
    - 24 bits: 8 bits × R, G and B
    - 32 bits: alpha channel for opacity
- **YUV**: brightness, R and B chrominance
    - PAL system, JPEG, MPEG
    - Color TV (B&W compatible)
- **HSL**: hue, saturation, and lightness

>

<https://en.wikipedia.org/wiki/RGB_color_model> <br/>
<https://en.wikipedia.org/wiki/YUV> <br/>
<https://en.wikipedia.org/wiki/HSL_and_HSV>

---

# ⭐ Raster File Formats

- *BMP*
    - (Normally) uncompressed image
- *TIFF, PNG*
    - *Lossless* compression
    - Reduced size, without deterioration
- *JPEG*
    - *Lossy* compression
    - Much smaller size, but image deteriorated

>

<https://en.wikipedia.org/wiki/BMP_file_format>

---

![small](http://fondinfo.github.io/images/repr/bmp-header.jpg)
# 🧪 BMP Format

``` text
FILE INFO HEADER (14)
2   File type (= “BM”)
4   File size (in bytes)
4   Reserved
4   Image offset (in bytes)
BITMAP INFO HEADER (40)
4   Structure size
4+4 Image width and height
2   Planes (not used)
2   Depth (bpp, bits per pixel)
4+4 Compression and img size (0 without compression)
4+4 Horiz. and vert. resolution (pixels per meter)
4+4 # colors in palette and # important colors
Palette (RGBQUAD)
4   Blue, Green, Red, Reserved
```

---

![small](http://fondinfo.github.io/images/repr/redbrick-grid.png)
[http://fondinfo.github.io/ <br> data/redbrick.bmp](http://fondinfo.github.io/data/redbrick.bmp)
# 🧪 Ex. Redbrick.BMP

![](http://fondinfo.github.io/images/repr/redbrick-dump.svg)

---

![small](http://fondinfo.github.io/images/repr/redbrick-grid.png)
![small](http://fondinfo.github.io/images/repr/redbrick-palette.svg)
# 🧪 Ex. Redbrick.BMP

```
row 0, scanline 31  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
row 1, scanline 30  00 00 00 00 00 00 00 00 09 00 00 00 00 00 00 00
row 2, scanline 29  11 11 01 19 11 01 10 10 09 09 01 09 11 11 01 90
...
row 31, scanline 0  99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 90
```

- Normal header: $54$ bytes
- Each color in palette: $4$ bytes
- Each row always occupies a multiple of 4 bytes (with *padding*)
- File size, in bytes

$$54 + 4\cdot colors + ⌈w\cdot bpp / 32⌉\cdot 4\cdot h$$

---

# 🧪 Reading BMP in Python

- Data as a *sequence of bytes*, type `bytes`

``` py
with open("redbrick.bmp", "rb") as bmp:
    head = bmp.read(54)
    img_pos = int.from_bytes(head[10:14], "little")
    head_len = int.from_bytes(head[14:18], "little") + 14
    w = int.from_bytes(head[18:22], "little")
    h = int.from_bytes(head[22:26], "little")
    bpp = int.from_bytes(head[28:30], "little")
    colors = (img_pos - head_len) // 4
    row_len = -4 * (w * bpp // -32)  # `ceil div`, 4-byte align
    bmp.read(head_len - 54)  # consume remaining header, if any
    palette = [bmp.read(4) for _ in range(colors)]
    image = [bmp.read(row_len) for _ in range(h)]
```

>

<https://fondinfo.github.io/play/?c14_bmp.py>

---

# 🧪 Drawing BMP in g2d

``` py
for i, v in enumerate(palette):
    print(f"Color {i:3}:", v.hex(" "))
for i, v in enumerate(image):
    print(f"Row {i:3}:", v.hex(" "))
```

``` py
for y, row in enumerate(reversed(image)):
    for x in range(w):
        if bpp == 4:
            pix = row[x // 2]  # 2 pixels per byte
            pix = pix // 16 if x % 2 == 0 else pix % 16
            b, g, r, _ = palette[pix]
            g2d.set_color((r, g, b))
        g2d.draw_rect((x, y), (1, 1))
```

>

<https://fondinfo.github.io/play/?c14_bmp.py>

---

![](http://fondinfo.github.io/images/repr/vector-example.svg)
# 💡️ Vector Graphics

- Image: set of geometric primitives
    - Lines, polygons..., colors, gradients...
- 👍 Quality, at various resolutions
- 👍 Data compression
- 👍 Modification management
- 👎 Not intuitive for some
- 👎 Potentially expensive
- 👎 Resources not known beforehand
- **Applications**: desktop publishing (DTP), video-editing, architecture, engineering, 3D graphics (CAD), vector fonts (scalable characters with good definition)

---

# ⭐ Vector File Formats

- *PS* (PostScript)
- *PDF* (Portable Document Format)
- *WMF* (Windows MetaFile)
- *TTF* (True Type Font)
- *CDR* (CorelDraw)
- *DXF* (AutoCAD)
- *SWF* (Flash)
- *SVG* (Scalable Vector Graphics, for the web)

>

<https://en.wikipedia.org/wiki/Scalable_Vector_Graphics>

---

![](http://fondinfo.github.io/images/repr/svg-example.svg)
# 🧪 SVG File Example

``` svg
<svg xmlns="http://www.w3.org/2000/svg"
    width="400" height="350">

  <circle cx="150" cy="200" r="140"
      fill="#ff0000"
      stroke="#000000" stroke-width="2" />

  <rect x="140" y="10" width="250" height="250" rx="40"
      fill="#0000ff" fill-opacity="0.6"
      stroke="#000000" stroke-width="2" />

</svg>
```

>

<http://fondinfo.github.io/data/svg-example.html>

---


![](http://fondinfo.github.io/images/repr/multimedia.png)
# Digital Audio

---

![](http://fondinfo.github.io/images/repr/sampled-signal.svg) ![](http://fondinfo.github.io/images/repr/digital-signal.svg)
# ⭐ Digital Audio

- Sound: waves of compression and rarefaction of air
    - Longitudinal oscillations, in direction of propagation
    - Audible spectrum: 20-20'000 Hz
- Analog quantity → discretization
    - **Sampling** in time
    - **Quantizing** of amplitudes
- *Nyquist-Shannon*: `$f_s \geq 2B$`
    - *CD-DA*: stereo, 44.1 kHz, 16 bits
    - *Voice* (G.711): mono, 8 kHz, 8 bits
    - ❓ What is the *byte rate* (bytes/s)? And the *bit rate* (bits/s)?

---

# ⭐ WAV Size

- How many bytes per sampling instant?
    - `$BlockAlign = NumChannels \cdot BitsPerSample / 8$`
- How many bytes per second?
    - `$ByteRate = SampleRate \cdot BlockAlign$`
- *Resource Interchange File Format*
    - Container for various multimedia data
    - WAV, AVI, ANI, RMI (midi), CDR, WebP...
- `size` fields: always reduced by 8 bytes
    - `id` and `size` fields themselves are not counted

>

<http://soundfile.sapp.org/doc/WaveFormat/>
<br>
<http://fondinfo.github.io/data/tada.wav>

---

# 🧪 WAV Format

![large](http://fondinfo.github.io/images/repr/wav-format.png)

---

# 🧪 WAV File Example

![large](http://fondinfo.github.io/images/repr/wav-bytes.svg)

---


![](http://fondinfo.github.io/images/repr/document-struct.png)
# Structured Documents

---

# 💡️ Structured Documents

- **Logical structure**
    - Determines the *role* of the various parts of the text
    - Titles, text, notes, etc.
- **Graphical structure**
    - Assigns a graphical rendering to the roles
    - Thus determines the overall graphical rendering of the document
    - "Prints" differently what has a different role
- **Word processing**: not so much *writing*, but *engineering information*

---

# 💡 WYSIWYG

- *What You See Is What You Get*
- Focus on graphics, losing sight of logical structure
    - Graphics: not with graphical commands...
    - But by defining the **styles** of the various parts of the doc, as logical *roles*
    - E.g. Word/Writer styles: “*Title*”, “*Footnote*”, “*Header*”
    - Not graphical names, but logical
- Alternatively: editing based on **commands** or **tags**

---

![](http://fondinfo.github.io/images/repr/w3c-keys.jpg)
# ⭐ HyperText Markup Language

- *Structured* *hypertext* documents
    - Can be created with *Notepad* etc.
- HTML defines *types* of elements
    - Paragraphs, links, multimedia…
- HTML **element** composed of three parts
    - **Opening tag**, **content**, **closing tag**
    - `Bla <i>in italics</i> bla`
- Many elements have **attributes** (key-value pairs)
    - `<a href="http://www.unipr.it/">UniPR</a>`
    - `id` and `class`: generic attributes for assigning *logical roles*
- There are also elements **without content**
    - `<img src="blueribbon.gif" />`


>

<http://fondinfo.github.io/data/html-example.html>

---

# ⭐ Anatomy of a Page

![large](http://fondinfo.github.io/images/repr/html-page.svg)

---

# 🧪 Text Formatting Tags

``` html
<h1>The largest title</h1>
…
<h6>The smallest title</h6>
<p>This is a paragraph.<br />Newline but same paragraph.</p>

<ul>
  <li>First item of an unordered list.</li>
  <li>Second item, <b>in bold</b>.</li>
</ul>

<div class="remark" id="r01">
  Generic block-level structure, with a
  generic <span class="techy">inline</span> element.
</div>
```

>

<https://html.spec.whatwg.org/>

---

![](http://fondinfo.github.io/images/repr/html5-logo.svg)
# 🧪 Html 5

- New HTML 5 structural elements
    - `header, main, nav, aside, footer`
    - `article, section, details, summary`
    - `menu, menuitem, figure, figcaption`
- Other new elements
    - `video, audio, canvas, embed`
    - `mark, time`
    - `output, progress, meter, datalist`

>

<https://www.w3.org/TR/html5-diff/#language>
<br>
<https://developer.mozilla.org/docs/Web/HTML/Element>

---

![large](http://fondinfo.github.io/images/sys/globe.jpg)
# 🔬 The World Wide Web

- *WWW* ≈ HTML + URL + HTTP
- *HTTP*: HyperText Transfer Protocol
    - Text-based protocol for transferring multimedia resources
- *URL*: Uniform Resource Locator
    - Reference to a resource on the network
    - For HTTP, includes: host; port (80); path; query (after `?`); fragment *id* (after `#`)

![](http://fondinfo.github.io/images/repr/uri-diagram.svg)
