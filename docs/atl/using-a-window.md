---
title: "Przy użyciu okna (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e4cc64dd524615c003619466f66f4bf92ab62f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-a-window"></a>Przy użyciu okna
Klasa [CWindow](../atl/reference/cwindow-class.md) umożliwia przy użyciu okna. Po podłączeniu okno, aby `CWindow` obiektu, można wywołać `CWindow` metoda manipulowania okna. `CWindow`zawiera także `HWND` operatora, aby przekonwertować `CWindow` do obiektu `HWND`. W związku z tym można przekazać `CWindow` obiektu dowolnej funkcji, które wymaga dojścia do okna. Można łatwo łączyć `CWindow` wywołania metody i wywołania funkcji Win32, bez tworzenia wszystkie obiekty tymczasowe.  
  
 Ponieważ `CWindow` ma tylko dwie danych elementu członkowskiego (uchwyt okna i wymiary domyślne), nie nakłada obciążenie kodu. Ponadto wiele `CWindow` metody po prostu zawijać odpowiedniej funkcji Win32 API. Za pomocą `CWindow`, `HWND` elementu członkowskiego jest automatycznie przekazany do funkcji Win32.  
  
 Oprócz używania `CWindow` bezpośrednio, użytkownik może również pochodzić od go, aby dodać dane lub kod do klasy. ATL sam pochodzi trzech klas z `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [cdialogimpl —](../atl/implementing-a-dialog-box.md), i [CContainedWindowT](../atl/using-contained-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

