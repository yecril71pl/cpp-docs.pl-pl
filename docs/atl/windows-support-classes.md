---
title: Windows obsługuje klas (ATL) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 40521ce5b7ec192781e1496590fdd42b36e132e1
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848392"
---
# <a name="windows-support-classes"></a>Klasy obsługi Windows
Następujące klasy obsługi dla systemu windows:  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md) zapewnia otoki dla `CreateWindow` i `CreateWindowEx`.  
  
-   [CWindow](../atl/reference/cwindow-class.md) zawiera metody do manipulowania okna. `CWindow` jest klasą bazową dla `CWindowImpl`, `CDialogImpl`, i `CContainedWindow`.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementuje okna, w oparciu o nowe klasy okna. Pozwala również na podklasę lub superklasie okna.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) implementuje okno dialogowe.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementuje okno dialogowe (modalnym lub niemodalnym), który obsługuje formanty ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementuje okno dialogowe (modalnym lub niemodalnym) z podstawowymi funkcjami.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) manipuluje okno które obsługuje formant ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) zapewnia metody do manipulowania okno które obsługuje formant ActiveX i ma również obsługę hostowania licencjonowane formanty ActiveX.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implementuje okno znajdujących się w innym obiekcie.  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) zarządza informacjami nowe klasy okna.  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md) obsługuje dynamiczne łańcuch mapy wiadomości.  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) umożliwia obiektu do udostępnienia komunikat mapuje do innych obiektów.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) zapewnia prostą metodę standaryzacji cech okna obiektu ATL.  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) zawiera wartości domyślne style okna ramowego i rozszerzone style używane można utworzyć okna. Te wartości są dodawane przy użyciu — operator logiczny OR wartości podane podczas tworzenia okna.  
  
## <a name="related-articles"></a>Powiązane artykuły  
 [Klasy okien ATL](../atl/atl-window-classes.md)  
  
 [ALT — samouczek](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../atl/atl-class-overview.md)   
 [Makra mapy komunikatów](../atl/reference/message-map-macros-atl.md)   
 [Makra klasy okna](../atl/reference/window-class-macros.md)

