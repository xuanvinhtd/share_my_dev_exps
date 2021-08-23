
```javascript
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