---
title: Używanie list obrazów w formancie paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: 81468528c15300a7e9ace6b20fd9fb34818f1928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366497"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Używanie list obrazów w formancie paska narzędzi

Domyślnie obrazy używane przez przyciski w formancie paska narzędzi są przechowywane jako pojedyncza mapa bitowa. Można jednak również przechowywać obrazy przycisków w zestawie list obrazów. Obiekt sterujący paska narzędzi może używać maksymalnie trzech oddzielnych list obrazów:

- Lista obrazów z włączoną obsługą Zawiera obrazy dla przycisków paska narzędzi, które są aktualnie włączone.

- Lista obrazów wyłączone Zawiera obrazy dla przycisków paska narzędzi, które są obecnie wyłączone.

- Wyróżniona lista obrazów Zawiera obrazy dla przycisków paska narzędzi, które są aktualnie wyróżnione. Ta lista obrazów jest używana tylko wtedy, gdy pasek narzędzi używa stylu TBSTYLE_FLAT.

Te listy obrazów są używane przez formant paska narzędzi podczas kojarzenia ich z obiektem. `CToolBarCtrl` To skojarzenie jest realizowane przez wykonywanie połączeń do [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)i [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

Domyślnie MFC używa `CToolBar` klasy do zaimplementowania pasków narzędzi aplikacji MFC. Jednak funkcja `GetToolBarCtrl` elementu członkowskiego może służyć do `CToolBarCtrl` pobierania osadzonego obiektu. Następnie można nawiązać `CToolBarCtrl` połączenia z funkcjami członkowskimi przy użyciu zwracany obiekt.

Poniższy przykład pokazuje tę technikę, przypisując`m_ToolBarImages`włączoną ( ) i wyłączoną`m_ToolBarDisabledImages` `CToolBarCtrl` ( ) listę obrazów do obiektu (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> Listy obrazów używane przez obiekt paska narzędzi muszą być obiektami trwałymi. Z tego powodu są one często elementy członkowskie danych klasy MFC; w tym przykładzie klasy okna ramki głównej.

Po skojarzeniu list obrazów `CToolBarCtrl` z obiektem struktura automatycznie wyświetla odpowiedni obraz przycisku.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
