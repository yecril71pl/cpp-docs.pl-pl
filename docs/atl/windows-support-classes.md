---
title: System Windows obsługuje klasy (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2095e5141dfdd320bae0e7aa69ffd4b3c9fe9a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362085"
---
# <a name="windows-support-classes"></a>Klasy obsługi systemu Windows
Następujące klasy zapewniają obsługę dla systemu windows:  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md) zapewnia otoki **właściwości CreateWindow** i **CreateWindowEx**.  
  
-   [CWindow](../atl/reference/cwindow-class.md) zawiera metody okna. `CWindow` jest klasą bazową dla `CWindowImpl`, `CDialogImpl`, i `CContainedWindow`.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementuje okna, w oparciu o nowe klasy okna. Można też do podklasy lub superklasie okna.  
  
-   [Cdialogimpl —](../atl/reference/cdialogimpl-class.md) implementuje okno dialogowe.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementuje okno dialogowe (modalne i niemodalne) obsługującego formantów ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementuje okno dialogowe (modalne i niemodalne) z podstawowymi funkcjami.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) manipuluje okna obsługującego formantu ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) udostępnia metody do manipulowania okna, które obsługuje formantu ActiveX ale ma także obsługa hostingu licencjonowane formanty ActiveX.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implementuje okna zawarty w innym obiekcie.  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) zarządza informacjami nową klasę okna.  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md) obsługuje dynamiczne tworzenie łańcuchów mapy komunikatów.  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) umożliwia mapuje obiektu do udostępnienia jej wiadomości do innych obiektów.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) zapewnia prostą metodę z standaryzacji cechy obiekt ATL okna.  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) zawiera wartości domyślne style okna i rozszerzone style używane można utworzyć okna. Te wartości są dodawane przy użyciu operatora logicznego OR, wartości podane podczas tworzenia okna.  
  
## <a name="related-articles"></a>Powiązane artykuły  
 [Klasy okien ATL](../atl/atl-window-classes.md)  
  
 [ALT — samouczek](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../atl/atl-class-overview.md)   
 [Makra mapy wiadomości](../atl/reference/message-map-macros-atl.md)   
 [Makra klasy okna](../atl/reference/window-class-macros.md)

