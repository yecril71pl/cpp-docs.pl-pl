---
title: Klasy obsługi Windows (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.windows
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: 9a33136c63c5bdc32dfc882e8c53ab2f5c27eb46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665416"
---
# <a name="windows-support-classes"></a>Klasy obsługi Windows

Następujące klasy obsługi dla systemu windows:

- [_U_MENUorID](../atl/reference/u-menuorid-class.md) zapewnia otoki dla `CreateWindow` i `CreateWindowEx`.

- [CWindow](../atl/reference/cwindow-class.md) zawiera metody do manipulowania okna. `CWindow` jest klasą bazową dla `CWindowImpl`, `CDialogImpl`, i `CContainedWindow`.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementuje okna, w oparciu o nowe klasy okna. Pozwala również na podklasę lub superklasie okna.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) implementuje okno dialogowe.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementuje okno dialogowe (modalnym lub niemodalnym), który obsługuje formanty ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementuje okno dialogowe (modalnym lub niemodalnym) z podstawowymi funkcjami.

- [CAxWindow](../atl/reference/caxwindow-class.md) manipuluje okno które obsługuje formant ActiveX.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) zapewnia metody do manipulowania okno które obsługuje formant ActiveX i ma również obsługę hostowania licencjonowane formanty ActiveX.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implementuje okno znajdujących się w innym obiekcie.

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) zarządza informacjami nowe klasy okna.

- [CDynamicChain](../atl/reference/cdynamicchain-class.md) obsługuje dynamiczne łańcuch mapy wiadomości.

- [CMessageMap](../atl/reference/cmessagemap-class.md) umożliwia obiektu do udostępnienia komunikat mapuje do innych obiektów.

- [CWinTraits](../atl/reference/cwintraits-class.md) zapewnia prostą metodę standaryzacji cech okna obiektu ATL.

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) zawiera wartości domyślne style okna ramowego i rozszerzone style używane można utworzyć okna. Te wartości są dodawane przy użyciu — operator logiczny OR wartości podane podczas tworzenia okna.

## <a name="related-articles"></a>Powiązane artykuły

[Klasy okien ATL](../atl/atl-window-classes.md)

[ALT — samouczek](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../atl/atl-class-overview.md)<br/>
[Makra mapy komunikatów](../atl/reference/message-map-macros-atl.md)<br/>
[Makra klasy okna](../atl/reference/window-class-macros.md)

