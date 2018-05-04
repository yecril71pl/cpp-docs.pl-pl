---
title: Przy użyciu okna (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f946f99fd198db281418e2a471489b2236972435
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="using-a-window"></a>Przy użyciu okna
Klasa [CWindow](../atl/reference/cwindow-class.md) umożliwia przy użyciu okna. Po podłączeniu okno, aby `CWindow` obiektu, można wywołać `CWindow` metoda manipulowania okna. `CWindow` zawiera także `HWND` operatora, aby przekonwertować `CWindow` do obiektu `HWND`. W związku z tym można przekazać `CWindow` obiektu dowolnej funkcji, które wymaga dojścia do okna. Można łatwo łączyć `CWindow` wywołania metody i wywołania funkcji Win32, bez tworzenia wszystkie obiekty tymczasowe.  
  
 Ponieważ `CWindow` ma tylko dwie danych elementu członkowskiego (uchwyt okna i wymiary domyślne), nie nakłada obciążenie kodu. Ponadto wiele `CWindow` metody po prostu zawijać odpowiedniej funkcji Win32 API. Za pomocą `CWindow`, `HWND` elementu członkowskiego jest automatycznie przekazany do funkcji Win32.  
  
 Oprócz używania `CWindow` bezpośrednio, użytkownik może również pochodzić od go, aby dodać dane lub kod do klasy. ATL sam pochodzi trzech klas z `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [cdialogimpl —](../atl/implementing-a-dialog-box.md), i [CContainedWindowT](../atl/using-contained-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

