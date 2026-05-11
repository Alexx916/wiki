## Screen & container sizes
Screen sizes are dictated by commonly used [screen widths](#Suggested%20width%20declarations), as seen in the table below. [Container widths](#Suggested%20container%20width%20declarations) will typically follow these, with a `max-width` declaration being assigned based on the design. The below sections go into further detail about screen and container sizing and the reasons behind these decisions.

### Suggested width declarations
This isn't exactly what tailwind uses for its widths (for example, a 1536px declaration is used for `screen-2xl`, likely due to this width having the [fourth largest market share in 2025](#Global%20screen%20market%20share%20(Nov%202024-2025))). As such, the above width declarations have been chosen to capture the most common breakpoints and ensure fluidity across devices.

| Tailwind declaration | Alias         | Screen width | Comment                                        |
| -------------------- | ------------- | ------------ | ---------------------------------------------- |
| xs (nonstandard)                  | mobile        | 360px        | Most popular mobile market share 2025 (19.18%) <br/> We don't use this as a vairable but this **must be the smallest size the design will properly display on** |
| sm                   | mobile-large  | 640px        | Tailwind default size                          |
| md                   | tablet        | 768px        | iPad portrait                                  |
| lg                   | tablet-large  | 1024px       | iPad landscape<br>Tailwind default size        |
| xl                   | laptop        | 1280px       | Laptop and above<br>Tailwind default size      |
| 2xl                  | laptop-large  | 1536px       | Macbook and above                              |
| 3xl  (nonstandard)               | desktop       | 1680px       | Desktop and above                              |
| 4xl  (nonstandard)                | desktop-large | 1920px       | UHD/4k screens                                 |

### Suggested container width declarations
Rather than having a set of widths for a container, Tailwind sets the maximum width of an element with the `container` class to match the minimum width of the current breakpoint, rather than supporting specific content widths. We are able to set a max-width on a case-by-case basis, however as a general rule content should adhere to a uniform set of widths.

The following container sizes are dictated by ourselves as a method of keeping containers relatively uniform whilst still allowing for variation. **The values themselves are not a golden rule**, as we don't want to look like we're designing [Every Fucking Bootstrap Website Ever](http://www.dagusa.com/), however it is important to use the variants to create a small container, a wide container, and a full width container to keep a natural flow of content.

| Alias      | Container min width | Container max width               | Tailwind declaration | Comment                                                                                                |
| ---------- | ------------------- | --------------------------------- | -------------------- | ------------------------------------------------------------------------------------------------------ |
| Small      | 1080px              | 1280px                            | container-small      | Used for walls of text to reduce eye movement.                                                         |
| Medium     | 1440px              | 1680wpx                           | container            | Typical content size for a given design.<br>*This should be considered the typical width for content.* |
| Large      | 1680px              | 100vw (minus global site padding) | container-wide       | Wider content **with container padding.**                                                              |
| Full Width | 100vw               | 100vw                             | container-full       | Full width banners **flush to the viewport.**                                                          |

## Column grids, spacing & gaps

Content is typically laid out using a **column grid** when coding in tailwind, with between 1 and 12 columns being used. These can be applied across breakpoints, e.g. a news archive may opt to have one column on mobile, two columns on tablet, and three columns on desktop. When applying these columns, a *gap* value will typically be applied alongside this, for example:

`<div class="grid grid-cols-3 gap-4"></div>` 

would result in a grid with three columns and a 16 pixel gap between each column.

<iframe height="500" width="500" scrolling="no" title="Tailwind" src="https://codepen.io/alexx916/embed/qEZerOd?default-tab=result" frameborder="no" allowtransparency="true"></iframe>

https://codepen.io/alexx916/embed/qEZerOd

Tailwind uses the same spacing scale for margin and padding values, alongside the gap between elements in a grid. The below scale shows these tailwind values up to 80px, as this is likely the largest gap you will need between content. 

| Tailwind declaration | Size (REM) | Size (Pixels) |
| -------------------- | ---------- | ------------- |
| 0                    | 0px        | 0px           |
| px                   | 1px        | 1px           |
| 0.5                  | 0.125rem   | 2px           |
| 1                    | 0.25rem    | 4px           |
| 1.5                  | 0.375rem   | 6px           |
| 2                    | 0.5rem     | 8px           |
| 2.5                  | 0.625rem   | 10px          |
| 3                    | 0.75rem    | 12px          |
| 3.5                  | 0.875rem   | 14px          |
| 4                    | 1rem       | 16px          |
| 5                    | 1.25rem    | 20px          |
| 6                    | 1.5rem     | 24px          |
| 7                    | 1.75rem    | 28px          |
| 8                    | 2rem       | 32px          |
| 9                    | 2.25rem    | 36px          |
| 10                   | 2.5rem     | 40px          |
| 11                   | 2.75rem    | 44px          |
| 12                   | 3rem       | 48px          |
| 14                   | 3.5rem     | 56px          |
| 16                   | 4rem       | 64px          |
| 20                   | 5rem       | 80px          |

Note that the larger the values get, the fewer values are in between (e.g. 12 to 14, skipping 13). This is to ensure values scale in an aesthetic manner rather than just supplying every possible option. Whilst it is possible for us to use arbitrary values, we need to reference these via the REM value rather than the tailwind class (for example, instead of using `gap-13` we'd need to write `gap-[3.25rem]`). 

As such, it's easier to adhere to the below values or, if you intend to use a custom value, keeping this global so we can create a "set and forget" using a custom class name rather than explicitly setting this every time we need it. Below are a couple of examples of how tailwind classes would be applied to an element or a section.

### Complete list of spacing values

| Tailwind declaration | Size (REM) | Size (Pixels) |
| -------------------- | ---------- | ------------- |
| base-0               |            | 0px           |
| base-px              |            | 1px           |
| base-05              | 0.125rem   | 2px           |
| base-1               | 0.25rem    | 4px           |
| base-15              | 0.375rem   | 6px           |
| base-2               | 0.5rem     | 8px           |
| base-25              | 0.625rem   | 10px          |
| base-3               | 0.75rem    | 12px          |
| base-35              | 0.875rem   | 14px          |
| base-4               | 1rem       | 16px          |
| base-5               | 1.25rem    | 20px          |
| base-6               | 1.5rem     | 24px          |
| base-7               | 1.75rem    | 28px          |
| base-8               | 2rem       | 32px          |
| base-9               | 2.25rem    | 36px          |
| base-10              | 2.5rem     | 40px          |
| base-11              | 2.75rem    | 44px          |
| base-12              | 3rem       | 48px          |
| base-14              | 3.5rem     | 56px          |
| base-16              | 4rem       | 64px          |
| base-20              | 5rem       | 80px          |
| base-24              | 6rem       | 96px          |
| base-28              | 7rem       | 112px         |
| base-32              | 8rem       | 128px         |
| base-36              | 9rem       | 144px         |
| base-40              | 10rem      | 160px         |
| base-44              | 11rem      | 176px         |
| base-48              | 12rem      | 192px         |
| base-52              | 13rem      | 208px         |
| base-56              | 14rem      | 224px         |
| base-60              | 15rem      | 240px         |
| base-64              | 16rem      | 256px         |
| base-72              | 18rem      | 288px         |
| base-80              | 20rem      | 320px         |
| base-96              | 24rem      | 384px         |


## Color declarations


| Name    | Value | Hexcode  |                    Default                    |
| ------- |:-----:| -------- |:---------------------------------------------:|
| lighter |  100  | \#dbeae3 | <input type="checkbox" unchecked id="c034ea"> |
| light   |  300  | \#add6c0 | <input type="checkbox" unchecked id="cac32d"> |
| base    |  500  | \#5bae82 | <input type="checkbox" unchecked id="14800d"> |
| dark    |  700  | \#006737 |  <input type="checkbox" checked id="6413aa">  |
| darker  |  900  | \#00472e | <input type="checkbox" unchecked id="874649"> |


| Declaration | Affected content       | 
| ----------- | ---------------------- |
| body        | Body text              |
| headings    | Headings               |
| links       | Anchor links           |
| strong      | Bold text              |
| bold        | Bold text              |
| counters    | Ordered list numbers   |
| bullets     | Unordered list bullets |
| hr          | Dividers               |
| captions    | Image captions         |

## Components


## Fonts

### Using clamp() for fluid type
Minimum and maximum clamps are dictated by screen widths as above, with mobile adhering to the `mobile` screen and desktop adhering to the `laptop-large` screen sizes as dictated in [Suggested screen width declarations](#Suggested%20screen%20width%20declarations). 

| Clamp declaration | Width (px) | Width (rem) | Width (screen) |
| ----------------- | ---------- | ----------- | -------------- |
| Min               | 640px      | 40rem       | mobile-large   |
| Max               | 1440px     | 90rem       | laptop-large   |

### Sizes

#### Headings

| Declaration | Min Clamp | Max Clamp | Min size (px) | Max size (px) |
| ----------- | --------- | --------- | ------------- | ------------- |
| h1          | 3rem      | 5rem      | 48px          | 80px          |
| h2          | 2.5rem    | 3.75rem   | 40px          | 60px          |
| h3          | 2rem      | 3rem      | 32px          | 48px          |
| h4          | 1.75rem   | 2.5rem    | 28px          | 40px          |
| h5          | 1.5rem    | 2rem      | 24px          | 32px          |
| h6          | 1.25rem   | 1.75rem   | 20px          | 28px          |

#### Body/Components

| Declaration | Min Clamp (rem) | Max Clamp (rem) | Min size (px) | Max size (px) |
| ----------- | --------------- | --------------- | ------------- | ------------- |
| lg          | 1.125           | 1.5             | 18            | 24            |
| base        | 0.875           | 1.25            | 14            | 20            |
| sm          | 0.75            | 1               | 12            | 16            |

## Scrollbars
Whilst most modern browsers have support for customising scrollbars, Firefox has very little support for this. With this in mind it's important to note that only minor changes to scrollbars will reflect across all browsers.

It is also important to bear in mind that different operating systems will render scrollbars in a different way.

## Research and References

### Screen size market share
#### Global screen market share (Nov 2024-2025)

| Screen Width | Screen Height | Market Share (%) |
| ------------ | ------------- | ---------------- |
| 1920         | 1080          | 8.33             |
| 360          | 800           | 6.82             |
| 390          | 844           | 3.86             |
| 1536         | 864           | 3.62             |
| 1366         | 768           | 3.44             |
| 393          | 873           | 3.35             |
| 375          | 812           | 2.78             |
| 412          | 915           | 2.54             |
| 800          | 600           | 2.48             |
| 384          | 832           | 2.33             |
| 393          | 852           | 2.25             |
| 360          | 780           | 2.15             |
| 414          | 896           | 2.12             |
| 1280         | 720           | 1.93             |
| 385          | 854           | 1.75             |
| 430          | 932           | 1.75             |
| 360          | 806           | 1.74             |
| 1440         | 900           | 1.36             |
| 428          | 926           | 1.27             |
| 2560         | 1440          | 1.23             |
| Other        |               | 42.9             |

#### Mobile screen width market share (Nov 2024-2025)

| Width | Market Share (%) |
| ----- | ---------------- |
| 360   | 19.18            |
| 393   | 10.44            |
| 390   | 6.31             |
| 384   | 6.21             |
| 375   | 5.98             |
| 412   | 5.74             |
| 414   | 3.48             |
| 430   | 2.87             |
| 385   | 2.68             |
| 428   | 2.08             |


#### Tablet screen width market share (Nov 2024-2025)

| Screen Width | Market Share (%) |
| ------------ | ---------------- |
| 768          | 16.27            |
| 810          | 10.25            |
| 800          | 9.66             |
| 820          | 8.68             |
| 1280         | 8.24             |
| 601          | 6.71             |
| 834          | 4.67             |
| 1024         | 3.24             |
| 744          | 3.17             |
| 686          | 2.09             |
| 1334         | 2.06             |
| 962          | 1.51             |
| 712          | 1.06             |
| 534          | 0.98             |
| 600          | 0.98             |

#### Desktop screen width market share (Nov 2024-2025)

| Screen Width | Market Share (%) |
| ------------ | ---------------- |
| 1920         | 22               |
| 1280         | 11.86            |
| 1536         | 9.65             |
| 1366         | 9.16             |
| 800          | 6.34             |
| 1440         | 3.62             |
| 2560         | 3.29             |
| 1600         | 2.06             |
| 3840         | 1.64             |
| 810          | 1.27             |
| 1680         | 1.02             |
| 1470         | 0.82             |
| 1024         | 0.78             |
