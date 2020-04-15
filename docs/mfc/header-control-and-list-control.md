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
ms.openlocfilehash: 53dd6f1a7878d82a7f7ac48dd7082d791323941b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370469"
---
# <a name="header-control-and-list-control"></a>Formant nagłówka i formant listy

W większości przypadków użyjesz formantu nagłówka, który jest osadzony w [CListCtrl](../mfc/reference/clistctrl-class.md) lub [CListView](../mfc/reference/clistview-class.md) obiektu. Istnieją jednak przypadki, w których pożądane jest oddzielne gołym okiem na nagłówek, takie jak manipulowanie danymi, rozmieszczone w kolumnach lub wierszach, w obiekcie cview.However, are in cases where a separate header control object is desirable, such as manipulating data, arranged in columns or rows, in a [CView](../mfc/reference/cview-class.md)-derived object. W takich przypadkach należy większą kontrolę nad wyglądem i domyślne zachowanie osadzonego formantu nagłówka.

W typowym przypadku, że chcesz formantu nagłówka, aby zapewnić standardowe, domyślne zachowanie, można użyć [CListCtrl](../mfc/reference/clistctrl-class.md) lub [CListView](../mfc/reference/clistview-class.md) zamiast. Użyj, `CListCtrl` jeśli chcesz, aby funkcja domyślnego formantu nagłówka, osadzone w widoku listy wspólnego formantu. Użyj [CListView,](../mfc/reference/clistview-class.md) jeśli chcesz funkcjonalność domyślnego formantu nagłówka, osadzone w obiekcie widoku.

> [!NOTE]
> Te formanty obejmują tylko wbudowany kontrolka nagłówka, jeśli formant widoku listy jest tworzony przy użyciu **stylu LVS_REPORT.**

W większości przypadków wygląd osadzonego formantu nagłówka można zmodyfikować, zmieniając style formantu widoku listy zawierającej. Ponadto informacje o formancie nagłówka można uzyskać za pośrednictwem funkcji członkowskich nadrzędnego widoku listy. Jednak w celu uzyskania pełnej kontroli i dostępu do atrybutów i stylów osadzonego formantu nagłówka zaleca się uzyskanie wskaźnika do obiektu formantu nagłówka.

Obiekt kontroli nagłówka osadzonego można uzyskać `CListCtrl` `CListView` dostęp z jednego lub wywołania funkcji `GetHeaderCtrl` elementu członkowskiego odpowiedniej klasy. Poniższy kod pokazuje to:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Korzystanie z list obrazów z kontrolkami nagłówka](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
