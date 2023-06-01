---
author: Kaushik Chemburkar
pubDatetime: 2023-06-01T20:04:00+11:00
title: Disable Dates in React-Calendar
postSlug: react-calendar
featured: false
draft: false
tags:
  - react
  - calendar
ogImage: ""
description:
  Disabling certain dates in React-Calendar.
---
A code snippet on how to disable certain dates by creating an array of date ranges in React-Calendar.

```javascript
import React, { useState } from 'react';
import Calendar from 'react-calendar';
import { isWithinInterval, isSameDay, parse } from 'date-fns';

function MyApp() {
  const [value, setValue] = useState(new Date());

  // Define the ranges and dates
  const disableDates = [
    { start: "2023-06-01", end: "2023-06-05" },
    { start: "2023-07-10", end: "2023-07-15" },
    "2023-08-20",
    "2023-09-25",
  ];

  function tileDisabled({ date, view }) {
    // Disable tiles in month view only
    if (view === 'month') {
      // Check if a date React-Calendar wants to check is within the disabled ranges or matches a disabled date
      return disableDates.some(disabled => {
        if (typeof disabled === 'string') {
          // If it's a string, treat it as a specific date to be disabled
          return isSameDay(date, parse(disabled, "yyyy-MM-dd", new Date()));
        } else {
          // Otherwise, treat it as a date range
          const start = parse(disabled.start, "yyyy-MM-dd", new Date());
          const end = parse(disabled.end, "yyyy-MM-dd", new Date());
          return isWithinInterval(date, { start, end });
        }
      });
    }
  }

  const onChange = newValue => {
    setValue(newValue);
  };

  return (
    <Calendar
      onChange={onChange}
      value={value}
      tileDisabled={tileDisabled}
    />
  );
}

export default MyApp;
```
