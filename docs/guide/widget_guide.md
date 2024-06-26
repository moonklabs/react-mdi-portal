# Widget Guide

### If you want to create a panel with the widget of your choice, please refer to this guide.

## Adding a new type when creating a panel

`src/components/NewWindowForm.js` file to allow you to select a new panel type.

```js
// src/modal/NewWindowForm.jsx
const windowData = {
  id: `temp-${Date.now()}`,
  width: 400,
  height: 300,
  x: 0,
  y: 0,
  isHide: false,
  isMaximize: false,
  isMinimize: false,
  isClose: false,
  isDrag: false,
  isResize: false,
  isClock: isClockChecked,
  isBrowser: isBrowserChecked,
  action: isBrowserChecked ? content : isClockChecked ? timezone : customApp,
  title,
  content: isBrowserChecked ? content : isClockChecked ? timezone : '',
  timezone: isClockChecked ? timezone : null,
  order: Date.now(),
};
```

> Add customContent to action, content, and create another checkbox for customContent.

## Define a new panel type

`src/components/PanelContent.js` file and define the new panel type like this

```js
// src/components/PanelContent.js

const PanelContent = ({ action, content, title, timezone, currentTime }) => {
  return (
    <Box
      sx={{
        height: '100%',
        borderWidth: '0 1px 1px 1px',
        borderColor: '#D3D3D3',
        borderStyle: 'solid',
      }}
    >
      {action === 'browser' ? (
        <iframe
          src={content}
          title={title}
          style={{ width: '100%', height: '100%', border: 'none' }}
        />
      ) : action === 'clock' ? (
        <div>
          <div>{timezone}</div>
          <Typography variant="h4">{currentTime}</Typography>
        </div>
      ) : action === 'customApp' ? (
        <CustomApp content={content} />
      ) : (
        <Typography variant="body1">Content goes here.</Typography>
      )}
    </Box>
  );
};

export default PanelContent;
```

## Writing CustomApp components

`src/components/CustomApp.js` file, and write the logic for your custom app.

```js
import React from 'react';

const CustomApp = ({ content }) => {
  // This is where you write the logic for your personal app.
  return (
    <div>
      <h2>Custom App</h2>
      <p>{content}</p>
    </div>
  );
};

export default CustomApp;
```

> Follow this guide to create a custom widget as a panel. If you want to create multiple custom widgets, you can modify the code based on this guide.

_If you encounter issues or find any errors while following the guide, please send an email._
