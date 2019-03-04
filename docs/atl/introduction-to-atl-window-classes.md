---
title: Wprowadzenie do klas okien ATL
ms.date: 11/04/2016
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
ms.openlocfilehash: 0c3bc70b5edfb089a6276003625b876d8c553dcb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301652"
---
# <a name="introduction-to-atl-window-classes"></a>Wprowadzenie do klas okien ATL

Następujące klasy ATL są przeznaczone do wdrożenia i manipulowania systemu windows:

- [CWindow](../atl/reference/cwindow-class.md) pozwala dołączyć uchwyt okna do `CWindow` obiektu. Następnie wywołaj `CWindow` metody do manipulowania okna.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) pozwala na implementowanie nowe okno i przetwarzać komunikaty z mapy komunikatów. Można utworzyć okna na podstawie nowych Windows klasy, superklasie istniejącej klasy lub podklasy istniejącego okna.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) pozwala na implementowanie modalne lub niemodalnego okna dialogowego pole i przetwarzania komunikatów za pomocą mapy komunikatów.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) jest wstępnie klasa, która implementuje okno mapę komunikatów, w której znajduje się w innej klasy. Za pomocą `CContainedWindowT` umożliwia scentralizowanie przetwarzanie komunikatów w jednej klasie.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) pozwala na implementowanie okno dialogowe (modalnym lub niemodalnym), który obsługuje formanty ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) pozwala na implementowanie modalne okno dialogowe z podstawowymi funkcjami.

- [CAxWindow](../atl/reference/caxwindow-class.md) pozwala na implementowanie okno które obsługuje formant ActiveX.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) pozwala na implementowanie okna, który jest hostem licencjonowany formant ActiveX.

Oprócz klas w określonym oknie ATL udostępnia kilka klas, które mają ułatwić implementacji obiektu okien ATL. Są one następujące:

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) zarządza informacjami nowe klasy okna.

- [CWinTraits](../atl/reference/cwintraits-class.md) i [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) umożliwiają proste standaryzacji cech obiektu ATL okna.

## <a name="see-also"></a>Zobacz także

[Klasy okien](../atl/atl-window-classes.md)
