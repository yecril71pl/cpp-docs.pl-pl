---
title: Formant nagłówka i formant listy
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: 934b54de3266138225087d5519af2be51972cf9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240078"
---
# <a name="header-control-and-list-control"></a>Formant nagłówka i formant listy

W większości przypadków, będą używać kontrolki nagłówka, który jest osadzony w [CListCtrl](../mfc/reference/clistctrl-class.md) lub [CListView](../mfc/reference/clistview-class.md) obiektu. Jednak istnieją przypadki, gdzie jest pożądane, takie jak manipulowanie danymi, uporządkowane wiersze lub kolumny w obiekt formantu nagłówka oddzielnych [CView](../mfc/reference/cview-class.md)-pochodnych obiektu. W takich przypadkach konieczne jest większą kontrolę nad wyglądem i domyślne zachowanie kontrolki nagłówka osadzonych.

W przypadku typowych mają kontrolki nagłówka, aby zapewnić standardowe, domyślne zachowanie, możesz chcieć użyć [CListCtrl](../mfc/reference/clistctrl-class.md) lub [CListView](../mfc/reference/clistview-class.md) zamiast tego. Użyj `CListCtrl` , aby funkcje domyślne kontrolki nagłówka, osadzonego w formancie wspólnego widoku listy. Użyj [CListView](../mfc/reference/clistview-class.md) , aby funkcje domyślne kontrolki nagłówka, osadzonego w obiekt widoku.

> [!NOTE]
>  Do tych kontrolek należą tylko formantu nagłówka wbudowanych, jeśli kontrolka widoku listy jest tworzony przy użyciu **LVS_REPORT** stylu.

W większości przypadków można zmodyfikować wygląd formantu osadzonego nagłówka, zmieniając stylów zawierającego kontrolka widoku listy. Ponadto informacje o formancie nagłówka można uzyskać za pośrednictwem funkcji składowych kontrolka widoku listy nadrzędnej. Jednak dla pełnej kontroli i dostępu do atrybutów i style kontrolki nagłówka osadzony, zalecane jest, uzyskać wskaźnik do obiektu kontrolki nagłówka.

Obiekt formantu osadzonego nagłówek jest możliwy z poziomu `CListCtrl` lub `CListView` przy użyciu wywołania do klasy odpowiednie `GetHeaderCtrl` funkcja elementu członkowskiego. Poniższy kod przedstawia to:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Używanie list obrazów z formantami nagłówka](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
