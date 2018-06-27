---
title: Używanie list obrazów w formancie paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50e7cb936c55ced1f16a325a031dccd1edde7d06
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951910"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Używanie list obrazów w formancie paska narzędzi
Domyślnie obrazy używane przez przycisków w formancie paska narzędzi są przechowywane jako pojedynczy mapy bitowej. Można jednak przechowywać obrazy dla przycisków w zestawie listy obrazów. Obiekt formantu paska narzędzi można używać do trzech list osobny obraz:  
  
-   Włączone obraz listy zawiera obrazy dla przycisków paska narzędzi, które są obecnie włączone.  
  
-   Wyłączone obraz listy zawiera obrazy dla przycisków paska narzędzi, które są obecnie wyłączone.  
  
-   Wyróżnione obraz listy zawiera obrazy dla przycisków paska narzędzi, które są aktualnie podświetlonej. Ta lista obrazu jest używana tylko wtedy, gdy styl TBSTYLE_FLAT korzysta z paska narzędzi.  
  
 Te listy obrazów są używane przez kontrolkę paska narzędzi po skojarzeniu ich z `CToolBarCtrl` obiektu. To skojarzenie odbywa się przy wywołaniach [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), i [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).  
  
 Domyślnie używa MFC `CToolBar` klasy do zaimplementowania pasków narzędzi aplikacji MFC. Jednak `GetToolBarCtrl` funkcji członkowskiej może służyć do pobierania osadzonego `CToolBarCtrl` obiektu. Następnie można wprowadzić wywołań `CToolBarCtrl` funkcje Członkowskie przy użyciu zwrócony obiekt.  
  
 W poniższym przykładzie pokazano ta technika, przypisując włączone (`m_ToolBarImages`), jak i wyłączonych (`m_ToolBarDisabledImages`) listy obrazów do `CToolBarCtrl` obiektu (`m_ToolBarCtrl`).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  Listy obrazów używane przez obiekt paska narzędzi musi być stały obiektów. Z tego powodu często są one elementy członkowskie danych klasy MFC; w tym przykładzie klasy okna w ramce głównej.  
  
 Po listy obrazów są skojarzone z `CToolBarCtrl` obiektu, w ramach automatycznie wyświetla obraz przycisku właściwe.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

