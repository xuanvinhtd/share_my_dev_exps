# Tip and Snippets

This page will help you quickly create a new component, import something by JUST COPY, PASTE, and customize it.

## New Compomemt vs function template

1. UI

- None props

[viewrn1.js](_snippets/rn/viewrn1.js.md ':include')

- Have props

[viewrn2.js](_snippets/rn/viewrn2.js.md ':include')


2. Function


[funcrn.js](_snippets/rn/funcrn.js.md ':include')


## Import Component and Use

1. Containers(Page)


```
import { MenuPage, LoginPage, AccountPage } from '@/Containers'
```

2. Componments

```
import { HeaderView, SectionMenu, RowMenu } from '@/Components'
```

3. Theme


```
import { useTheme, AppFonts, ResponsiveFont, Colors } from '@/Theme'
const { Common, Layout, Images } = useTheme()
```

4. Translation


```
import { useTranslation } from 'react-i18next'
const { t } = useTranslation()
```

5. React Component


```
import React, { useState, useEffect, useRef } from 'react'
import { Image, Text, StyleSheet } from 'react-native'
useEffect(() => {}, [])
```


6. Redux


```
import { useDispatch, useSelector } from 'react-redux'
const dispatch = useDispatch()
const userInfo = useSelector(state => state.user.userInfo)
```

7. Style vs Font

- Use font:

[fontrn.js](_snippets/rn/fontrn.js.md ':include')

!> Don't define more font to use! If you have an exception, please confirm với Teamleader

- Style:
?> Use `ResponsiveFont` to Responsive Font for mobile and tablet or iPad
?> Use `hp vs wp` to Responsive UI for mobile and tablet or iPad
- [responsive screen package](https://www.npmjs.com/package/react-native-responsive-screen)


[styledevice.js](_snippets/rn/styledevice.js.md ':include')

?> [Sample and demo Layout Flexbox](https://reactnative.dev/docs/flexbox)

[stylern.js](_snippets/rn/stylern.js.md ':include')

## Cheat Sheet

- [Cheat sheet RN](https://devhints.io/react)

?> Updating....