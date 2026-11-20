# Text Scroller 🎭

A simple subtitle paging tool built for our high school production of *Les Misérables*.

Text Scroller lets a subtitle operator follow the performers' pace by manually advancing lyrics or dialogue with the mouse wheel. Built with Python and Tkinter, it displays centered white text on a black background for rehearsals and stage projection.

## Behind the Project

I worked on the production team and played **Éponine** in our high school staging of *Les Misérables*. Building this subtitle tool was part of my contribution to the show.

Here are two recordings of my performances as Éponine:

- [**On My Own** · Watch on Bilibili](https://www.bilibili.com/video/BV1Cu4TzCEWH/)
- [**A Little Fall of Rain** · Watch on Bilibili](https://www.bilibili.com/video/BV1yM4Tz5EGj/)

## Features

- **Manual paging:** scroll down to advance and up to return to the previous group of subtitles.
- **Large, centered text:** white text on a black background, using 40-point Times New Roman by default.
- **Plain-text input:** edit subtitles directly in the UTF-8 encoded `x.txt` file.
- **Simple setup:** uses Python's standard-library Tkinter interface, with no third-party Python packages required. Your Python installation must include Tk support.

## Getting Started

### 1. Check Your Python Setup

Install Python 3, then check that Tkinter is available:

```bash
python -m tkinter
```

A test window should open. If Python reports that `tkinter` is missing, install or enable Tk support for your Python environment.

### 2. Download the Project

```bash
git clone https://github.com/ClaireFuzzy/Text-Scroller.git
cd Text-Scroller
```

Alternatively, select **Code → Download ZIP** on GitHub, extract the archive, and open a terminal in the project folder.

### 3. Prepare Your Subtitles and Run

Edit `x.txt` in the project folder and save it with **UTF-8** encoding. Then run:

```bash
python main_2.py
```

The program loads `x.txt` using a relative path, so run it from the folder containing that file. Restart the program after editing the subtitles to load your changes.

## Controls

Place your mouse pointer inside the application window and use the scroll wheel:

| Action | Result |
| --- | --- |
| Scroll down | Show the next group of subtitles |
| Scroll up | Show the previous group of subtitles |
| Close the window | Exit the program |

By default, each group contains **13 lines from the source file**, and each scroll advances or rewinds by 13 lines. The operator controls the timing manually; there is no automatic audio or timeline synchronization.

## Subtitle Format

`x.txt` is a plain-text file split by line breaks. For example:

```text
First subtitle in English
Translation of the first subtitle

Second subtitle in English
Translation of the second subtitle
```

You can use subtitles in one language or arrange bilingual lines in the order you want them displayed. Blank lines count toward the group size. Long lines wrap automatically, so 13 source lines may occupy more than 13 lines on screen.

## Customization

Edit the following settings in `main_2.py`:

| Setting | Default | Where to Change It |
| --- | --- | --- |
| Window size | `800x600` | `root.geometry("800x600")` |
| Font and size | Times New Roman, 40 pt | `font=("Times New Roman", 40)` |
| Lines per group and scroll step | `13` | `lines_per_scroll=13` in `TextScroller.__init__` |
| Subtitle file | `x.txt` | `file_path = "x.txt"` |
| Text and background colors | White on black | The text widget's `fg` and `bg` arguments |

Before a performance, connect the actual projector and run through the complete subtitle file. Adjust the window size, font size, and lines per group so that long lines and bilingual subtitles remain fully visible.

## Project Files

```text
Text-Scroller/
├── main_2.py    # Subtitle display and mouse-wheel paging
├── x.txt        # Subtitle text loaded by the program
├── data.pdf     # Included PDF; not read by the program
└── README.md
```

## Current Limitations

- No timeline synchronization, keyboard paging shortcuts, page jumping, or separate operator preview window.
- The program binds Tkinter's `<MouseWheel>` event. Mouse-wheel behavior varies across operating systems, and the binding may need adjustment on Linux.
- The final group may repeat some lines from the previous group because of how the program positions the last page.
- Scrolling down with fewer total lines than the configured group size may display unexpected results. For short files, set `lines_per_scroll` to a positive integer no larger than the total number of lines.

---

Made for our high school stage, to help the subtitles keep pace with every entrance and every song.
