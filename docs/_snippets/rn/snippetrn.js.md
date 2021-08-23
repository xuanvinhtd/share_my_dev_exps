```javascript

//  1. Containers(Page)

import { MenuPage, LoginPage, AccountPage } from '@/Containers'

//  2. Componments

import { HeaderView, SectionMenu, RowMenu } from '@/Components'

// 3. Theme

import { useTheme, AppFonts, ResponsiveFont, Colors } from '@/Theme'
const { Common, Layout, Images } = useTheme()

// 4. Translation

import { useTranslation } from 'react-i18next'
const { t } = useTranslation()

// 5. React Component

import React, { useState, useEffect, useRef } from 'react'
import { Image, Text, StyleSheet } from 'react-native'

useEffect(() => {}, [])


// 6. Redux

import { useDispatch, useSelector } from 'react-redux'
const dispatch = useDispatch()
const userInfo = useSelector(state => state.user.userInfo)

```