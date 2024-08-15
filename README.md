# React-spread-sheet-excel
A high-performance React component for building Excel-like spreadsheets with advanced features.

A light weight component to Render large lists of input boxes in the table using React JS and Redux, Render a table with a large number of rows and columns.
Able to render 1Lakh+ input boxes in react, A quick solution for web based spreadsheet or excel.

[![npm version](https://badge.fury.io/js/react-spread-sheet-excel.svg)](https://badge.fury.io/js/react-spread-sheet-excel) ![Downloads](https://img.shields.io/npm/dm/react-spread-sheet-excel.svg)
  <a href="https://codecov.io/gh/sojinantony01/react-spread-sheet" > 
 <img src="https://codecov.io/gh/sojinantony01/react-spread-sheet/graph/badge.svg?token=OLGA3TDJIL"/> 
 </a>
  <a href="https://github.com/sojinantony01/react-spread-sheet/blob/main/LICENSE">
    <img src="https://img.shields.io/npm/l/react-spread-sheet-excel.svg" alt="license">
  </a>

## [Live demo](https://sojinantony01.github.io/react-spread-sheet/)

![alt text](https://raw.githubusercontent.com/sojinantony01/react-spread-sheet/main/public/images/samplesheet.png)


* Blazing Fast Rendering: Handles large datasets efficiently.
* Comprehensive Calculation Engine: Supports complex formulas and calculations. (= 2 * A2 + (B2 * C4))
* Rich Formatting Options: Customize cell appearance with bold, italic, underline, and more.
* Calculations Support, value should starts with "="
* Select Multiple cells
* Intuitive Keyboard Navigation: Navigate and edit cells effortlessly.
* Delete values in selected cells.
* Customizable header values - (Do not pass numbers in header values, will affect calc)
* Resize columns
* Can Use as a Spreadsheet or Excel with react
* Flexible Data Management: Import, export, and manipulate data.
* Customizable Headers and Columns: Tailor the spreadsheet to your application.
* Read-Only Mode: Protect data from accidental modifications.
* CSV Export: Easily share data in a common format.
* Sticky Headers: Keep headers visible while scrolling.
* 100% Unit Test Coverage: Ensures reliability and stability.
* JSON based

## Getting Started

Input data format
```json
[
  [{value: 1},{value: 1},{value: "a"},{value: "b"},{value: "d"}]
]
```
```
npm install react-spread-sheet-excel

```
## Example

```js
import React, { useRef, useState } from "react";
import Sheet, { SheetRef } from "./lib";
import packageConf from "../package.json";

const createData = () => {
  const val: any[][] = [];
  for (let i = 0; i < 2000; i++) {
    val.push(Array.from({ length: 40 }, () => Math.floor(Math.random() * 10)));
  }
  return val;
};
function App() {
  const [state] = useState<any[][]>(createData());
  const childRef = useRef<SheetRef>(null);
  const onChange = (i: number, j: number, value: string) => {
    //Do not try to update state with this action, it will slow down your application
    console.log(`Value Updated at ${j}, ${j}`, value);
  };
  const getData = () => {
    console.log("Updated Data", childRef?.current?.getData()); 
  };

  return (
    <div>
      <div>
        <button onClick={getData}>Get Updated data</button>
      </div>
      <div>
        <Sheet data={state} onChange={onChange} ref={childRef} />
      </div>
    </div>
  );
}

export default App;


```
## props

| Prop | Description | Default | Mandatory | type
| --- | --- | -- | -- | -- |
| data | Array of array with values (matrix)  | [[]]  |  No | any[][] |
| onChange | Calls when a change is detected in input boxes, Do not set render component when value changes, the component should be uncontrolled |  | No | 
| resize | show column resize option | false | No | boolean |
| hideXAxisHeader | Show serial numbers in X axis | false | No | boolean |
| hideYAxisHeader | Show serial numbers in Y axis | false | No | boolean |
| headerValues | array of header values, Number in header values could affect calculations | alphabets | No | string[] |
| hideTools | Hide tools | false | No | boolean |


## Ref

| Ref | Description |
| --- | --- |
| getData | Get updated data from sheet | 
| setData | Set new data to sheet |

Performance
Benchmark: Rendered 1000 rows and 100 columns in milli seconds.
Optimization Techniques: Redux, Lazy loading.


[Sojin Antony](https://github.com/sojinantony01)


[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-1.svg)](https://www.buymeacoffee.com/sojinantony)

## Acknowledgments

* React-intersection-observer
* Redux, React Redux
