---
title: Wprowadzenie do klas okien ALT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea9b275831aee3ea96da1036019db07f9e2dfc93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356689"
---
# <a name="introduction-to-atl-window-classes"></a>Wprowadzenie do klas okien ALT
Następujące klasy ATL są przeznaczone do wdrożenia i manipulowania systemu windows:  
  
-   [CWindow](../atl/reference/cwindow-class.md) umożliwia dołączanie uchwyt okna do `CWindow` obiektu. Następnie wywołaj `CWindow` metoda manipulowania okna.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) umożliwia wdrożenie nowe okno i przetwarzać komunikaty z mapy komunikatów. Można utworzyć okna oparte na nowe klasy systemu Windows, superklasie istniejącej klasy lub podklasy istniejącego okna.  
  
-   [Cdialogimpl —](../atl/reference/cdialogimpl-class.md) umożliwia wdrożenie po zakończeniu instalacji lub niemodalnego okna dialogowego proces i pola wiadomości z mapy komunikatów.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) jest klasą wbudowane, który implementuje okno mapę komunikatów w której znajduje się w innej klasy. Przy użyciu `CContainedWindowT` pozwala na scentralizowanie przetwarzania komunikatu w jednej klasie.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) umożliwia implementuje okno dialogowe (modalne i niemodalne) obsługującego formantów ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) umożliwia wdrożenie modalne okno dialogowe z podstawowymi funkcjami.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) umożliwia zaimplementować okno obsługującego formantu ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) umożliwia wdrożenie okna, który jest hostem licencjonowanego formantu ActiveX.  
  
 Oprócz klasy określone okno ATL udostępnia kilka klas zaprojektowanych w celu ułatwienia implementacji obiektu okna ATL. Są one następujące:  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) zarządza informacjami nową klasę okna.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) i [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) Podaj to prosta metoda standaryzacji cechy obiekt ATL okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

