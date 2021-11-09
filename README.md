
# Tabs module

* [General info](#general-info)
* [Technologies](#technologies)
* [Setup](#setup)

## JS stucture
```

function tabs(tabsSelector, tabsItemSelector, tabsContentSelector, activeClass) {

	const tabsWrapper = document.querySelector(tabsSelector),
		tabs = tabsWrapper.querySelectorAll(tabsItemSelector),
		tabsContent = document.querySelectorAll(tabsContentSelector);


	function hideElements() {
		tabsContent.forEach(item => {
			item.classList.remove('show', 'fade');
		});
		tabs.forEach(tab => {
			tab.classList.remove(activeClass);
		});
	}
	function showElements(i = 0) {
		tabsContent[i].classList.add('show', 'fade');

		tabs[i].classList.add(activeClass);
	}

	hideElements();
	showElements();

	function checkIfClickedTargetOnItem(e) {
		//Для последующего удобного использования
		const target = e.target;
		//проверяем на target, чтобы отсеить элементы которые не имееют обьекта target 

		if (target && target.classList.contains(tabsItemSelector.substring(1))) {
			tabs.forEach((item, i) => {
				if (target == item) {
					hideElements();
					showElements(i);
				}
			});
		}
	}
	tabsWrapper.addEventListener('click', checkIfClickedTargetOnItem);
}

export default tabs;
```

