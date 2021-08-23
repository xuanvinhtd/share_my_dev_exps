```javascript
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