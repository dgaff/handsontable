---
title: 'Referencing the Handsontable instance in React'
metaTitle: 'Referencing the Handsontable instance in React - Guide - Handsontable Documentation'
permalink: /12.0/react-hot-reference
canonicalUrl: /react-hot-reference
---

# Referencing the Handsontable instance in React

## Overview

The following example implements the `@handsontable/react`component showing how to reference the Handsontable instance from the wrapper component.

## Example

::: example #example1 :react
```jsx
import React, { useRef } from 'react';
import ReactDOM from 'react-dom';
import { HotTable } from '@handsontable/react';
import { registerAllModules } from 'handsontable/registry';
import { createSpreadsheetData } from './helpers';

// register Handsontable's modules
registerAllModules();

const hotSettings = {
  data: createSpreadsheetData(4, 4),
  colHeaders: true,
  height: 'auto',
  licenseKey: 'non-commercial-and-evaluation'
};

const App = () => {
  const hotTableComponent = useRef(null);

  const swapHotData = () => {
    // The Handsontable instance is stored under the `hotInstance` property of the wrapper component.
    hotTableComponent.current.hotInstance.loadData([['new', 'data']]);
  };

  return (
    <div className="controls">
      <HotTable ref={hotTableComponent} settings={hotSettings}/>
      <br/>
      <button onClick={swapHotData}>Load new data!</button>
    </div>
  );
}

ReactDOM.render(<App/>, document.getElementById('example1'));
```
:::
