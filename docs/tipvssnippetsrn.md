# Tip and Snippets

This page will help you quickly create a new component, import something by JUST COPY, PASTE, and customize it.

## New Compomemt vs function template

1. UI

- None props

```
import React from 'react'
import { View } from 'react-native'

const YourView = () => {
  return <View />
}

const styles = StyleSheet.create({})

export default YourView
```

- Have props
```
import React from 'react'
import { View } from 'react-native'

const YourView = props => {
  const { style, disabled = false, onPress, children } = props;
  return <View />
}

const styles = StyleSheet.create({})
YourView.propTypes = {
  items: PropTypes.array,
  onItemPress: PropTypes.func,
  title: PropTypes.string,
}

YourView.defaultProps = {
  items: [],
  title: '',
  onItemPress: item => {},
}

export default YourView
```

2. Function

```
 const resetUserName = () => {}
const onLogin = async () => {
}
const onGameItemPress = ({ id }) => {
}
```


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

```
...AppFonts.textCondensedBold,
...AppFonts.textCondensedBlack,
...AppFonts.textRegular,
...AppFonts.textMedium,
```
!> Don't define more font to use! If you have an exception, please confirm với Teamleader

- Style:
?> Use `ResponsiveFont` to Responsive Font for mobile and tablet or iPad
?> Use `hp vs wp` to Responsive UI for mobile and tablet or iPad
- [responsive screen package](https://www.npmjs.com/package/react-native-responsive-screen)

```
import DeviceInfo from 'react-native-device-info'
let isTablet = DeviceInfo.isTablet()
import {
  widthPercentageToDP as wp,
  heightPercentageToDP as hp,
} from 'react-native-responsive-screen'
```

?> [Sample and demo Layout Flexbox](https://reactnative.dev/docs/flexbox)

```
const styles = StyleSheet.create({
  itemContainer: {
    width: size,
    height: size,
    marginTop: wp('0.3%'),
    marginBottom: isTablet ? hp('5%') : hp('3.2%'),
  },
  topRightMark: {
    ...StyleSheet.absoluteFillObject,
    alignSelf: 'flex-end',
    marginTop: isTablet ? hp('-1.6%') : hp('-0.4%'),
    position: 'absolute',
    width: isTablet ? hp('27%') : wp('33%'),
    height: isTablet ? hp('6%') : hp('3.4%'),
  },
  centerMark: {
    ...StyleSheet.absoluteFillObject,
    position: 'absolute',
    marginLeft: wp('1.6%'),
    marginTop: isTablet ? wp('4.5%') : wp('2%'),
    width: wp('23%'),
    height: hp('9%'),
  },
  itemIcon: {
    flex: 1,
    width: size - 20,
    alignSelf: 'center',
  },
  sectionTitle: {
    ...AppFonts.textCondensedBlack,
    marginTop: wp('4%'),
    marginLeft: wp('4%'),
    marginBottom: wp('4%'),
    color: Colors.title,
    fontSize: ResponsiveFont(16),
  },
  // Use to show a text below an icon
  itemTitle: {
    ...StyleSheet.absoluteFillObject,
    bottom: '-20%',
    textAlign: 'center',
    alignSelf: 'center',
    marginTop: wp('24%'),
    color: Colors.menuTitle,
    fontSize: ResponsiveFont(10.5),
    ...AppFonts.textCondensedBold,
  },
  firstTitle: {
    ...StyleSheet.absoluteFillObject,
    bottom: '-20%',
    textAlign: 'center',
    alignSelf: 'center',
    marginTop: wp('24%'),
    color: Colors.title,
    fontSize: ResponsiveFont(10.5),
    ...AppFonts.textCondensedBold,
  },
})
```

## Cheat Sheet

- [Cheat sheet RN](https://devhints.io/react)

?> Updating....