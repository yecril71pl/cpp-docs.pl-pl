---
title: Kontrolka nagłówka i kontrolka listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24d40ea26a6ff52490b4a501a8b62c0aace660b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407637"
---
# <a name="header-control-and-list-control"></a>Kontrolka nagłówka i kontrolka listy

W większości przypadków, będą używać kontrolki nagłówka, który jest osadzony w [CListCtrl](../mfc/reference/clistctrl-class.md) lub [CListView](../mfc/reference/clistview-class.md) obiektu. Jednak istnieją przypadki, gdzie jest pożądane, takie jak manipulowanie danymi, uporządkowane wiersze lub kolumny w obiekt formantu nagłówka oddzielnych [CView](../mfc/reference/cview-class.md)-pochodnych obiektu. W takich przypadkach konieczne jest większą kontrolę nad wyglądem i domyślne zachowanie kontrolki nagłówka osadzonych.

W przypadku typowych mają kontrolki nagłówka, aby zapewnić standardowe, domyślne zachowanie, możesz chcieć użyć [CListCtrl](../mfc/reference/clistctrl-class.md) lub [CListView](../mfc/reference/clistview-class.md) zamiast tego. Użyj `CListCtrl` , aby funkcje domyślne kontrolki nagłówka, osadzonego w formancie wspólnego widoku listy. Użyj [CListView](../mfc/reference/clistview-class.md) , aby funkcje domyślne kontrolki nagłówka, osadzonego w obiekt widoku.

> [!NOTE]
>  Do tych kontrolek należą tylko formantu nagłówka wbudowanych, jeśli kontrolka widoku listy jest tworzony przy użyciu **LVS_REPORT** stylu.

W większości przypadków można zmodyfikować wygląd formantu osadzonego nagłówka, zmieniając stylów zawierającego kontrolka widoku listy. Ponadto informacje o formancie nagłówka można uzyskać za pośrednictwem funkcji składowych kontrolka widoku listy nadrzędnej. Jednak dla pełnej kontroli i dostępu do atrybutów i style kontrolki nagłówka osadzony, zalecane jest, uzyskać wskaźnik do obiektu kontrolki nagłówka.

Obiekt formantu osadzonego nagłówek jest możliwy z poziomu `CListCtrl` lub `CListView` przy użyciu wywołania do klasy odpowiednie `GetHeaderCtrl` funkcja elementu członkowskiego. Poniższy kod przedstawia to:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Używanie list obrazów z formantami nagłówka](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

