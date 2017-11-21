---
title: "System Windows obsługuje klasy (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.windows
dev_langs: C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96ca4417cea6b4bdd1107d3f5d7b4ea9d85269e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="windows-support-classes"></a>Klasy obsługi systemu Windows
Następujące klasy zapewniają obsługę dla systemu windows:  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md) zapewnia otoki **właściwości CreateWindow** i **CreateWindowEx**.  
  
-   [CWindow](../atl/reference/cwindow-class.md) zawiera metody okna. `CWindow`jest klasą bazową dla `CWindowImpl`, `CDialogImpl`, i `CContainedWindow`.  
  
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
 [Klasy okien ALT](../atl/atl-window-classes.md)  
  
 [ALT — samouczek](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../atl/atl-class-overview.md)   
 [Makra mapy wiadomości](../atl/reference/message-map-macros-atl.md)   
 [Makra klasy okna](../atl/reference/window-class-macros.md)

