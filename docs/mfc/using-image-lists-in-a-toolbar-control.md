---
title: Używanie list obrazów w formancie paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: d027f7834c67ad0ed51d1b7fda5b2704972efe38
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300794"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Używanie list obrazów w formancie paska narzędzi

Domyślnie obrazy używane przy użyciu przycisków w formancie paska narzędzi są przechowywane jako postaci bitmapy. Jednak można również przechowywać obrazy przycisków w zestawie list obrazów. Obiekt formantu paska narzędzi można użyć do trzech list osobny obraz:

- Włączone obraz lista zawiera obrazy dla przycisków paska narzędzi, które są obecnie włączone.

- Wyłączone obraz lista zawiera obrazy dla przycisków paska narzędzi, które są obecnie wyłączone.

- Wyróżnione obraz lista zawiera obrazy dla przycisków paska narzędzi, które obecnie są wyróżnione. Ta lista obrazów jest używana tylko wtedy, gdy styl TBSTYLE_FLAT korzysta z paska narzędzi.

Te listy obrazów są używane przez kontrolkę paska narzędzi po skojarzeniu z `CToolBarCtrl` obiektu. To skojarzenie odbywa się przez wykonywanie wywołań do [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), i [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

Domyślnie, MFC wykorzystuje `CToolBar` klasy do zaimplementowania pasków narzędzi aplikacji MFC. Jednak `GetToolBarCtrl` funkcji składowej może służyć do pobierania osadzonego `CToolBarCtrl` obiektu. Następnie można prowadzić rozmowy `CToolBarCtrl` funkcji elementów członkowskich przy użyciu zwróconego obiektu.

W poniższym przykładzie pokazano tej techniki, przypisując włączony (`m_ToolBarImages`), jak i wyłączonych (`m_ToolBarDisabledImages`) listy obrazów do `CToolBarCtrl` obiektu (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
>  Listy obrazów, używane przez obiekt paska narzędzi musi być trwałe obiekty. Z tego powodu często są one elementów członkowskich danych klasy MFC; w tym przykładzie klasa głównej ramki okna.

Gdy list obrazów są skojarzone z `CToolBarCtrl` obiektu, w ramach automatycznie wyświetla obraz odpowiednie przycisku.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
