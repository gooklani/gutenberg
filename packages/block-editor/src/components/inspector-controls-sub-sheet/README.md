# InspectorControlsSubSheet

Inspector Controls Sub Sheet allows for adding controls inside the React Native bottom sheet settings. 

### Usage

```jsx
/**
 * External dependencies
 */
import { SafeAreaView, View } from 'react-native';

/**
 * WordPress dependencies
 */
import { InspectorControlsSubSheet } from '@wordpress/block-editor';
import { useNavigation } from '@react-navigation/native';
import { useState } from '@wordpress/element';
import { Icon, chevronRight } from '@wordpress/icons';

/**
 * Internal dependencies
 */
import Cell from '../bottom-sheet/cell';
import NavigationHeader from '../bottom-sheet/navigation-header';

const ExampleControl = () => {
	const [ showSubSheet, setShowSubSheet ] = useState( false );
	const navigation = useNavigation();

	const goBack = () => {
		setShowSubSheet( false );
		navigation.goBack();
	};

	const openSubSheet = () => {
		navigation.navigate( InspectorControlsSubSheet.screenName );
		setShowSubSheet( true );
	};

	return (
		<InspectorControlsSubSheet
			button={
				<Cell
					label={ 'Howdy' }
					separatorType="none"
					onPress={ openSubSheet }
				>
					<Icon icon={ chevronRight }></Icon>
				</Cell>
			}
			showSheet={ showSubSheet }
		>
			<SafeAreaView>
				<NavigationHeader
					screen={ 'Howdy' }
					leftButtonOnPress={ goBack }
				/>
				<View paddingHorizontal={ 16 }>
					<Text>{ 'World' }</Text>
				</View>
			</SafeAreaView>
		</InspectorControlsSubSheet>
	);
};

export default ExampleControl;
```

### Props

#### showSheet

Controls the Sub Sheet content visibility.

-   Type: `Boolean`
-   Required: Yes

#### navigationButton

UI rendered to allow navigating to the Sub Sheet when tapped.

-   Type: `ReactComponent`
-   Required: Yes


#### isFullScreen

Toggles the Sub Sheet height filling the entire device height.

-   Type: `Boolean`
-   Required: Yes

See `BottomSheetSelectControl` as an example.