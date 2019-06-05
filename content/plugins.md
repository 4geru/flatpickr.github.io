+++
date = "2017-03-25T20:23:43-05:00"
title = "Plugins"
weight = "9"
+++

Plugins are essentially a set of [hooks](/events/#hooks), that receive an optional config object and a [flatpickr instance](/instance-methods-properties-elements/).

Functionality requested by users that doesn't make it to core usually ends up in a plugin. The `flatpickr` repo comes with a few [plugins](https://github.com/chmln/flatpickr/tree/master/src/plugins).

## `confirmDate`

Provides a visual cue for users after selecting either:

- date + time
- multiple dates

```js
{
    "enableTime": true,
    "plugins": [new confirmDatePlugin({})]
}
```

<input class=flatpickr type="text" placeholder="Select Date.." data-id="confirmDate">

A spiffy SVG icon is included, along with sane defaults, but you can customize them.

Here are all the available options:

```js
{
    confirmIcon: "<i class='fa fa-check'></i>", // your icon's html, if you wish to override
    confirmText: "OK ",
    showAlways: false,
    theme: "light" // or "dark"
}
```

## `weekSelect`

For selecting a week.

```js
flatpickr({
    "plugins": [new weekSelect({})],
    "onChange": [function(){
        // extract the week number
        // note: "this" is bound to the flatpickr instance
        const weekNumber = this.selectedDates[0]
            ? this.config.getWeek(this.selectedDates[0])
            : null;

        console.log(weekNumber);
    }]
});


```

<input class=flatpickr type="text" placeholder="Select Date.." data-id="weekSelect">

## `rangePlugin (beta)`

Range selection using two inputs.

```js
flatpickr({
    "plugins": [new rangePlugin({ input: "#secondRangeInput"})]
});


```

<div style="display: flex; margin-top: 1.6rem">
 <div style="width: 49%; max-width: 300px; margin-right: 1em"   >
<label><div><b>Date 1</b></div>
<input class=flatpickr type="text" placeholder="Select Date.." data-id="rangePlugin"></label></div>
<div style="width: 49%; max-width: 300px;">
<label><div><b>Date 2</b></div>
<input type="text" placeholder="Select Date.." id="secondRangeInput"></label></div>
</div>

## `MinMaxTimePlugin (beta)`

Custom minTime and maxTime per date.

```js
{
    enableTime: true,
    minDate: "2025",
    plugins: [
        new minMaxTimePlugin({
            table: {
                "2025-01-10": {
                    minTime: "16:00",
                    maxTime: "22:00"
                }
            }
        })
    ]
};

```
<input class=flatpickr type="text" placeholder="Select Date.." data-id="minMaxTimePlugin">

## `monthSelectPlugin`

Show a month-only calendar view

```js
{
    plugins: [
        new monthSelectPlugin({
          shorthand: true, //defaults to false
          dateFormat: "m.y", //defaults to "F Y"
          altFormat: "F Y", //defaults to "F Y"
          theme: "dark" // defaults to "light"
        })
    ]
};

```
<input class=flatpickr type="text" placeholder="Select Date.." data-id="monthSelectPlugin">

