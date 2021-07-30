<div align="center">

  <h1>
    <br/>
    🏇
    <br />
    @choc-ui/chakra-autocomplete
    <br />
    <br />
  </h1>
  <sup>
    <br />
    <br />
    <a href="https://www.npmjs.com/package/@choc-ui/chakra-autocomplete?style=for-the-badge">
       <img src="https://img.shields.io/npm/v/@choc-ui/chakra-autocomplete.svg?style=for-the-badge" alt="npm package" />
    </a>
    <a href="https://www.npmjs.com/package/@choc-ui/chakra-autocomplete?style=for-the-badge">
      <img src="https://img.shields.io/npm/dw/@choc-ui/chakra-autocomplete.svg?style=for-the-badge" alt="npm  downloads" />
    </a>
<a>
    <img alt="NPM" src="https://img.shields.io/npm/l/@choc-ui/chakra-autocomplete?style=for-the-badge">
</a>

<a><img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/anubra266/choc-autocomplete?logo=github&style=for-the-badge">

<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->

[![All Contributors](https://img.shields.io/badge/all_contributors-3-orange.svg?style=flat-square)](#contributors-)

<!-- ALL-CONTRIBUTORS-BADGE:END -->

</a>
    <br />
    AutoComplete Component for the <a href="https://chakra-ui.com">Chakra UI</a> Library.</em>
    
  </sup>
  <br />
  <br />
  <br />
  <br />
  <pre>npm i <a href="https://www.npmjs.com/package/@choc-ui/chakra-autocomplete">@choc-ui/chakra-autocomplete</a></pre>
  <br />
  <br />
  <br />
  <br />
  <br />
</div>

## Install

```bash
npm i --save @choc-ui/chakra-autocomplete
#or
yarn add @choc-ui/chakra-autocomplete
```

## Preview

### With Mouse

![](./assets/mouse.gif)

### With Keyboard

![](./assets/keyboard.gif)

## Usage

### Basic Usage

```js
import { Flex, FormControl, FormHelperText, FormLabel } from "@chakra-ui/react";
import * as React from "react";
import {
  AutoComplete,
  AutoCompleteInput,
  AutoCompleteItem,
  AutoCompleteList,
} from "@choc-ui/chakra-autocomplete";

function App() {
  const countries = [
    "nigeria",
    "japan",
    "india",
    "united states",
    "south korea",
  ];

  return (
    <Flex pt="48" justify="center" align="center" w="full">
      <FormControl w="60">
        <FormLabel>Olympics Soccer Winner</FormLabel>
        <AutoComplete openOnFocus>
          <AutoCompleteInput variant="filled" />
          <AutoCompleteList>
            {countries.map((country, cid) => (
              <AutoCompleteItem
                key={`option-${cid}`}
                value={country}
                textTransform="capitalize"
              >
                {country}
              </AutoCompleteItem>
            ))}
          </AutoCompleteList>
        </AutoComplete>
        <FormHelperText>Who do you support.</FormHelperText>
      </FormControl>
    </Flex>
  );
}

export default App;
```

<img width="792" alt="CleanShot 2021-07-28 at 23 47 57@2x" src="https://user-images.githubusercontent.com/30869823/127406028-1b20b6c7-d2f4-4a27-a0f4-2a07598e7dfa.png">

### Creating Groups

You can create groups with the `AutoCompleteGroup` Component, and add a title with the `AutoCompleteGroupTitle` component.

```js
import { Flex, FormControl, FormHelperText, FormLabel } from "@chakra-ui/react";
import * as React from "react";
import {
  AutoComplete,
  AutoCompleteGroup,
  AutoCompleteGroupTitle,
  AutoCompleteInput,
  AutoCompleteItem,
  AutoCompleteList,
} from "@choc-ui/chakra-autocomplete";

function App() {
  const continents = {
    africa: ["nigeria", "south africa"],
    asia: ["japan", "south korea"],
    europe: ["united kingdom", "russia"],
  };

  return (
    <Flex pt="48" justify="center" align="center" w="full">
      <FormControl w="60">
        <FormLabel>Olympics Soccer Winner</FormLabel>
        <AutoComplete openOnFocus>
          <AutoCompleteInput variant="filled" />
          <AutoCompleteList>
            {Object.entries(continents).map(([continent, countries], co_id) => (
              <AutoCompleteGroup key={co_id} showDivider>
                <AutoCompleteGroupTitle textTransform="capitalize">
                  {continent}
                </AutoCompleteGroupTitle>
                {countries.map((country, c_id) => (
                  <AutoCompleteItem
                    key={c_id}
                    value={country}
                    textTransform="capitalize"
                  >
                    {country}
                  </AutoCompleteItem>
                ))}
              </AutoCompleteGroup>
            ))}
          </AutoCompleteList>
        </AutoComplete>
        <FormHelperText>Who do you support.</FormHelperText>
      </FormControl>
    </Flex>
  );
}

export default App;
```

<img width="661" alt="CleanShot 2021-07-29 at 01 18 47@2x" src="https://user-images.githubusercontent.com/30869823/127412483-89639ae2-34a7-4f59-9da0-287cd83cd035.png">

## Accessing the internal state

To access the internal state of the `AutoComplete`, use a function as children (commonly known as a render prop). You'll get access to the internal state `isOpen`, with the `onOpen` and `onClose` methods.

```js
import {
  Flex,
  FormControl,
  FormHelperText,
  FormLabel,
  Icon,
  InputGroup,
  InputRightElement,
} from "@chakra-ui/react";
import * as React from "react";
import {
  AutoComplete,
  AutoCompleteInput,
  AutoCompleteItem,
  AutoCompleteList,
} from "@choc-ui/chakra-autocomplete";
import { FiChevronRight, FiChevronDown } from "react-icons/fi";

function App() {
  const countries = [
    "nigeria",
    "japan",
    "india",
    "united states",
    "south korea",
  ];

  return (
    <Flex pt="48" justify="center" align="center" w="full">
      <FormControl w="60">
        <FormLabel>Olympics Soccer Winner</FormLabel>
        <AutoComplete openOnFocus>
          {({ isOpen }) => (
            <>
              <InputGroup>
                <AutoCompleteInput variant="filled" placeholder="Search..." />
                <InputRightElement
                  children={
                    <Icon as={isOpen ? FiChevronRight : FiChevronDown} />
                  }
                />
              </InputGroup>
              <AutoCompleteList>
                {countries.map((country, cid) => (
                  <AutoCompleteItem
                    key={`option-${cid}`}
                    value={country}
                    textTransform="capitalize"
                  >
                    {country}
                  </AutoCompleteItem>
                ))}
              </AutoCompleteList>
            </>
          )}
        </AutoComplete>
        <FormHelperText>Who do you support.</FormHelperText>
      </FormControl>
    </Flex>
  );
}

export default App;
```

<img width="1002" alt="CleanShot 2021-07-29 at 01 29 46@2x" src="https://user-images.githubusercontent.com/30869823/127413256-053d280f-46b7-4b12-bc49-c482963b857f.png">

## Custom Rendering

You can Render whatever you want. The `AutoComplete` Items are regular `Chakra` Boxes.

```js
import {
  Avatar,
  Flex,
  FormControl,
  FormHelperText,
  FormLabel,
  Text,
} from "@chakra-ui/react";
import * as React from "react";
import {
  AutoComplete,
  AutoCompleteInput,
  AutoCompleteItem,
  AutoCompleteList,
} from "@choc-ui/chakra-autocomplete";

function App() {
  const people = [
    { name: "Dan Abramov", image: "https://bit.ly/dan-abramov" },
    { name: "Kent Dodds", image: "https://bit.ly/kent-c-dodds" },
    { name: "Segun Adebayo", image: "https://bit.ly/sage-adebayo" },
    { name: "Prosper Otemuyiwa", image: "https://bit.ly/prosper-baba" },
    { name: "Ryan Florence", image: "https://bit.ly/ryan-florence" },
  ];

  return (
    <Flex pt="48" justify="center" align="center" w="full" direction="column">
      <FormControl id="email" w="60">
        <FormLabel>Olympics Soccer Winner</FormLabel>
        <AutoComplete openOnFocus>
          <AutoCompleteInput variant="filled" />
          <AutoCompleteList>
            {people.map((person, oid) => (
              <AutoCompleteItem
                key={`option-${oid}`}
                value={person.name}
                textTransform="capitalize"
                align="center"
              >
                <Avatar size="sm" name={person.name} src={person.image} />
                <Text ml="4">{person.name}</Text>
              </AutoCompleteItem>
            ))}
          </AutoCompleteList>
        </AutoComplete>
        <FormHelperText>Who do you support.</FormHelperText>
      </FormControl>
    </Flex>
  );
}

export default App;
```

<img width="541" alt="CleanShot 2021-07-29 at 01 35 03@2x" src="https://user-images.githubusercontent.com/30869823/127413575-9cea8ee8-3fd3-4720-8d87-7e1f996144be.png">

## Multi Select with Tags

Add the `multiple` prop to `AutoComplete` component, the `AutoCompleteInput` will now expose the tags in it's children function.
The `onChange` prop now returns an array of the chosen `values`

Now you can map the tags with the `AutoCompleteTag` component or any other component of your choice. The `label` and the `onRemove` method are now exposed.

```js
import { Flex, FormControl, FormHelperText, FormLabel } from "@chakra-ui/react";
import * as React from "react";
import {
  AutoComplete,
  AutoCompleteInput,
  AutoCompleteItem,
  AutoCompleteList,
  AutoCompleteTag,
} from "@choc-ui/chakra-autocomplete";

function App() {
  const countries = [
    "nigeria",
    "japan",
    "india",
    "united states",
    "south korea",
  ];

  return (
    <Flex pt="48" justify="center" align="center" w="full" direction="column">
      <FormControl id="email" w="60">
        <FormLabel>Olympics Soccer Winner</FormLabel>
        <AutoComplete openOnFocus multiple onChange={vals => console.log(vals)}>
          <AutoCompleteInput variant="filled">
            {({ tags }) =>
              tags.map((tag, tid) => (
                <AutoCompleteTag
                  key={tid}
                  label={tag.label}
                  onRemove={tag.onRemove}
                />
              ))
            }
          </AutoCompleteInput>
          <AutoCompleteList>
            {countries.map((country, cid) => (
              <AutoCompleteItem
                key={`option-${cid}`}
                value={country}
                textTransform="capitalize"
                _selected={{ bg: "whiteAlpha.50" }}
                _focus={{ bg: "whiteAlpha.100" }}
              >
                {country}
              </AutoCompleteItem>
            ))}
          </AutoCompleteList>
        </AutoComplete>
        <FormHelperText>Who do you support.</FormHelperText>
      </FormControl>
    </Flex>
  );
}

export default App;
```

![Kapture 2021-07-29 at 02 05 53](https://user-images.githubusercontent.com/30869823/127415996-09a5df7c-a356-4a22-ad9c-60d09963cfc6.gif)

## Creatable Items

I know that title hardly expresses the point, but yeah, naming is tough. You might want your users to be able to add extra items when their options are not available in the provided options. e.g. adding a new tag to your Polywork profile.

First add the `creatable` prop to the `AutoComplete` component.
Then add the `AutoCompleteCreatable` component to the bottom of the list. Refer to the references for more info on this component.

<img width="517" alt="CleanShot 2021-07-29 at 02 29 20@2x" src="https://user-images.githubusercontent.com/30869823/127417453-e78b9b48-26e8-4ff0-a264-1d6bb4717ab0.png">

## API Reference

**NB**: Feel free to request any additional `Prop` in [Issues](https://github.com/anubra266/choc-autocomplete/issues/new/).

### **AutoComplete**

Wrapper and Provider for `AutoCompleteInput` and `AutoCompleteList`

**AutoComplete** composes [**Box**](https://chakra-ui.com/docs/layout/box) so you can pass all Box props to change its style.

**NB:** None of the props passed to it are required.

```ts
export type UseAutoCompleteProps = Partial<{
  closeOnBlur: boolean; //close suggestions when input is blurred - true
  closeOnSelect: boolean; //close suggestions when a suggestions is selected - true
  creatable: boolean; //Allow addition of arbitrary values not present in suggestions - false
  defaultIsOpen: boolean; //Suggestions list is open by default -- false
  emphasize: boolean | CSSObject; //Highlight matching characters in suggestions, you can pass the styles - false
  emptyState: boolean | MaybeRenderProp<{ value: Item["value"] }>; //render message when no suggestions match query
  filter: (query: string, itemValue: Item["value"]) => boolean; //custom filter function
  focusInputOnSelect: boolean; //focus input after a suggestion is selected - true
  freeSolo: boolean; //allow entering of any values
  maxSelections: number //limit possible number of tag selections in multiple mode
  maxSuggestions: number; //limit number of suggestions in list
  multiple: boolean; //allow tags multi selection - false
  onChange: (value: string | Item["value"][]) => void; //function to run whenever autocomplete value(s) changes
  onSelectOption: (params: {
    optionValue: string;
    selectMethod: "mouse" | "keyboard" | null;
    isNewInput: boolean;
  }) => boolean | void; //method to call whenever a suggestion is selected
  onOptionFocus: (params: {
    optionValue: string;
    selectMethod: "mouse" | "keyboard" | null;
    isNewInput: boolean;
  }) => boolean | void;//method to call whenever a suggestion is focused
  onTagRemoved: (removedTag: Item["value"], tags: Item["value"][]) => void; //method to call whenever a tag is removed
  openOnFocus: boolean; //open suggestions when input is focuses -false
  rollNavigation: boolean; //allow keyboard navigation to switch to alternate ends when one end is reached
  selectOnFocus: boolean; //select the text in input when it's focused. - false
  shouldRenderSuggestions: (value: string) => boolean; //function to decide if suggestions should render, e.g. show suggestions only if there are at least two characters in the query value
  suggestWhenEmpty: boolean; //show suggestions when input value is empty - false
}>;
}
```

### **AutoCompleteTag**

Tags for multiple mode

**AutoCompleteTag** composes [**Tag**](https://chakra-ui.com/docs/data-display/tag) so you can pass all Tag props to change its style.

<table>
<thead>
  <tr>
    <th>Prop<br></th>
    <th>Type</th>
    <th>Description</th>
    <th>Required</th>
    <th>Default</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>label</td>
    <td>

    string

  </td>
    <td>Label that is displayed on the tag</td>
    <td>Yes<br></td>
    <td>&mdash;&mdash;&mdash;</td>
  </tr>
  <tr>
    <td>onRemove</td>
    <td>

```ts
() => void
```

  </td>
    <td>Method to remove the tag from selected values</td>
    <td>Yes<br></td>
    <td>&mdash;&mdash;&mdash;</td>
  </tr>
 
</tbody>
</table>

### **AutoCompleteInput**

Input for `AutoComplete` value.

**AutoCompleteInput** composes [**Input**](https://chakra-ui.com/docs/form/input) so you can pass all Input props to change its style.

<table>
<thead>
  <tr>
    <th>Prop<br></th>
    <th>Type</th>
    <th>Description</th>
    <th>Required</th>
    <th>Default</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>children</td>
    <td>

```ts
type children = MaybeRenderProp<{
  tags: { label: string; onRemove: () => void }[];
}>;
```

  </td>
    <td>

callback that returns `ReactNode` and is provided with tags in `multiple` mode
e.g.

```js
<AutoCompleteInput variant="filled">
  {({ tags }) =>
    tags.map((tag, tid) => (
      <AutoCompleteTag key={tid} label={tag.label} onRemove={tag.onRemove} />
    ))
  }
</AutoCompleteInput>
```

  </td>
    <td>No<br></td>
    <td>&mdash;&mdash;&mdash;</td>
  </tr>
 
</tbody>
</table>

### **AutoCompleteList**

Wrapper for `AutoCompleteGroup` and `AutoCompleteItem`

**AutoCompleteList** composes [**Box**](https://chakra-ui.com/docs/layout/box) so you can pass all Box props to change its style.

### **AutoCompleteGroup**

Wrapper for collections of `AutoCompleteItem`s

**AutoCompleteGroup** composes [**Box**](https://chakra-ui.com/docs/layout/box) so you can pass all Box props to change its style.

<Table>
<thead>
  <tr>
    <th>Prop<br></th>
    <th>Type</th>
    <th>Description</th>
    <th>Required</th>
    <th>Default</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>showDivider</td>
    <td>boolean</td>
    <td>If true, a divider is shown</td>
    <td>No</td>
    <td>false</td>
  </tr>

  <tr>
    <td>dividerColor</td>
    <td>string</td>
    <td>Color for divider, if present</td>
    <td>No</td>
    <td>inherit</td>
  </tr>
</tbody>

</table>

### **AutoCompleteItem**

This Composes your suggestions

**AutoCompleteItem** composes [**Flex**](https://chakra-ui.com/docs/layout/flex) so you can pass all Flex props to change its style.

<table>
<thead>
  <tr>
    <th>Prop<br></th>
    <th>Type</th>
    <th>Description</th>
    <th>Required</th>
    <th>Default</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>value</td>
    <td>string</td>
    <td>The value of the Option</td>
    <td>yes<br></td>
    <td>&mdash;&mdash;&mdash;</td>
  </tr>
  <tr>
    <td>fixed</td>
    <td>

    boolean

</td>
    <td>Make an item visible at all times, regardless of filtering</td>
    <td>No</td>
    <td>&mdash;&mdash;&mdash;</td>
</tr>
<tr>
    <td>_fixed</td>
    <td>

    CSSObject

</td>
    <td>Styles for fixed Itemm</td>
    <td>No</td>
    <td>

```js
{
  fontWeight: 'extrabold',
}
```

</td>
</tr>
<tr>
    <td>value</td>
    <td>string</td>
    <td>The value of the Option</td>
    <td>yes<br></td>
    <td>&mdash;&mdash;&mdash;</td>
  </tr>
  <tr>
    <td>disabled</td>
    <td>

    boolean

</td>
    <td>Make an item disabled, so it cannot be selected</td>
    <td>No</td>
    <td>&mdash;&mdash;&mdash;</td>
</tr>
<tr>
    <td>_disabled</td>
    <td>

    CSSObject

</td>
    <td>Styles for disabled Item(s)</td>
    <td>No</td>
    <td>

```js
{
  fontWeight: 'extrabold',
}
```

</td>
</tr>
<tr>
    <td>_selected</td>
    <td>

    CSSObject

</td>
    <td>Styles for selected Item(s)</td>
    <td>No</td>
    <td>

```js
{
  fontWeight: 'extrabold',
}
```

</td>
</tr>
<tr>
    <td>_focus</td>
    <td>

    CSSObject

</td>
    <td>Styles for focused Item</td>
    <td>No</td>
    <td>

```js
{
  fontWeight: 'extrabold',
}
```

</td>
</tr> 
</tbody>
</table>

### **AutoCompleteCreatable**

Used with the `AutoComplete` component's `creatable` prop, to allow users enter arbitrary values, not available in the provided options.

**AutoCompleteCreatable** composes [**Flex**](https://chakra-ui.com/docs/layout/flex) so you can pass all Flex props to change its style.

It also accepts a function as its `children` prop which is provided with the current `inputValue`.

<table>
<thead>
  <tr>
    <th>Prop<br></th>
    <th>Type</th>
    <th>Description</th>
    <th>Required</th>
    <th>Default</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>children</td>
    <td>

```ts
type children = MaybeRenderProp<{ value: any }>;
```

  </td>
    <td>

`ReactNode` or callback that returns `ReactNode`
e.g.

```js
<AutoCompleteCreatable>
  {({ value }) => <span>Add {value} to List</span>}
</AutoCompleteCreatable>
```

  </td>
    <td>No<br></td>
    <td>&mdash;&mdash;&mdash;</td>
  </tr>
 
</tbody>
</table>
## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://anubra266.tk"><img src="https://avatars.githubusercontent.com/u/30869823?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Abraham</b></sub></a><br /><a href="https://github.com/anubra266/choc-autocomplete/commits?author=anubra266" title="Code">💻</a></td>
    <td align="center"><a href="http://margalit.com.au"><img src="https://avatars.githubusercontent.com/u/2268424?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Sam Margalit</b></sub></a><br /><a href="https://github.com/anubra266/choc-autocomplete/commits?author=margalit" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/gepd"><img src="https://avatars.githubusercontent.com/u/7091609?v=4?s=100" width="100px;" alt=""/><br /><sub><b>gepd</b></sub></a><br /><a href="https://github.com/anubra266/choc-autocomplete/commits?author=gepd" title="Code">💻</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!