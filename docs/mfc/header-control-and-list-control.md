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
ms.openlocfilehash: f9dd34b27ddbdc0b99fafbb23ad1cf9782d98605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626420"
---
# <a name="header-control-and-list-control"></a>Formant nagłówka i formant listy

W większości przypadków będziesz używać kontrolki nagłówka osadzonej w obiekcie [CListCtrl](reference/clistctrl-class.md) lub [CListView](reference/clistview-class.md) . Istnieją jednak przypadki, w których pożądany jest oddzielny obiekt sterowania nagłówkami, taki jak manipulowanie danymi, ułożone w kolumnach lub wierszach w obiekcie pochodnym [CView](reference/cview-class.md). W takich przypadkach potrzebna jest większa kontrola nad wyglądem i domyślnym zachowaniem osadzonego formantu nagłówka.

W typowej sytuacji, gdy chcesz, aby kontrolka nagłówka zapewniała standardowe, domyślne zachowanie, możesz zamiast tego użyć [CListCtrl](reference/clistctrl-class.md) lub [CListView](reference/clistview-class.md) . Użyj `CListCtrl` , gdy chcesz, aby funkcja domyślnego formantu nagłówka była osadzona w widoku listy. Użyj [CListView](reference/clistview-class.md) , jeśli chcesz, aby funkcja domyślnego formantu nagłówka była osadzona w obiekcie widoku.

> [!NOTE]
> Te kontrolki zawierają tylko wbudowaną kontrolkę nagłówka, Jeśli kontrolka widok listy jest tworzona przy użyciu stylu **LVS_REPORT** .

W większości przypadków wygląd osadzonego formantu nagłówka można zmodyfikować, zmieniając style zawierające kontrolkę widok listy. Ponadto informacje o formancie nagłówka można uzyskać za pomocą funkcji Członkowskich formantu widoku listy nadrzędnej. Jednak w celu zapewnienia pełnej kontroli i dostępu do atrybutów i stylów osadzonego formantu nagłówka zaleca się uzyskanie wskaźnika do obiektu formantu nagłówka.

Do osadzonego obiektu formantu nagłówka można uzyskać dostęp z `CListCtrl` lub `CListView` z wywołaniem do `GetHeaderCtrl` funkcji składowej odpowiedniej klasy. Poniższy kod ilustruje:

[!code-cpp[NVC_MFCControlLadenDialog#14](codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Używanie list obrazów z kontrolkami nagłówka](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](using-cheaderctrl.md)<br/>
[Formanty](controls-mfc.md)
