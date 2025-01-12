# Introduction

A simple yet powerful and extensible **React Markdown Editor** that aims to have feature parity with the Github Markdown editor.
React-mde-headless has **no 3rd party dependencies**.

## [Demo](https://codesandbox.io/s/competent-jepsen-qyz51q?file=/src/index.tsx)

## Installing

    npm i react-headless-mde

## Using

```jsx
import { boldCommand, italicCommand, linkCommand, useTextAreaMarkdownEditor } from 'react-mde-headless';

export const MarkdownEditor = () => {
  const { ref, commandController } = useTextAreaMarkdownEditor({
    commandMap: {
      bold: boldCommand,
      italic: italicCommand,
      link: linkCommand,
    },
  });

  return (
    <div>
      <button
        onClick={() => {
          commandController.executeCommand('bold');
        }}
      >
        B
      </button>

      <textarea ref={ref} />
    </div>
  );
};
```

## Supported commands

- headingLevel1
- headingLevel2
- headingLevel3
- headingLevel4
- headingLevel5
- headingLevel6
- quote
- checkedList
- orderedList
- unorderedList
- bold
- code
- codeBlock
- italic
- strikethrough
- image
- link

## Todo

- heading undo
- undo/redo
- Check execution on SSR (For example, Next.js) and, if necessary, regenerate eslint config, taking into account execution on node.js
- peerDependencies React?
- undo for
  - 1st priority
    - all headings
    - quote
    - strikethrough
  - 2nd priority
    - orderedList
    - unorderedList
    - checkedList
    - codeBlock

PR's are welcome!

### Third party

- https://github.com/grassator/insert-text-at-cursor by https://twitter.com/d_kubyshkin

### XSS concerns

React-mde-headless does not automatically sanitize the HTML preview. If you are using Showdown,
this has been taken from [their documentation](<https://github.com/showdownjs/showdown/wiki/Markdown's-XSS-Vulnerability-(and-how-to-mitigate-it)>):

> Cross-side scripting is a well known technique to gain access to private information of the users
> of a website. The attacker injects spurious HTML content (a script) on the web page which will read
> the user’s cookies and do something bad with it (like steal credentials). As a countermeasure,
> you should filter any suspicious content coming from user input. Showdown does not include an
> XSS filter, so you must provide your own. But be careful in how you do it…

You might want to take a look at [showdown-xss-filter](https://github.com/VisionistInc/showdown-xss-filter).

## Licence

React-mde-headless is [MIT licensed](https://github.com/andrerpena/react-mde/blob/master/LICENSE).

## About the authors

Created by [André Pena](https://github.com/andrerpena). Maintained and developed by https://github.com/webbrother.
