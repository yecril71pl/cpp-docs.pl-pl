---
title: Korzystanie z okna (ATL) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 44b9988c0ecde4d0aee917fea686ec6511473318
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37847927"
---
# <a name="using-a-window"></a>Korzystanie z okna
Klasa [CWindow](../atl/reference/cwindow-class.md) pozwala korzystać z okna. Po podłączeniu okno, aby `CWindow` obiektu, a następnie możesz wywołać `CWindow` metody do manipulowania okna. `CWindow` zawiera także HWND operatora konwersji `CWindow` obiektu HWND. Ten sposób można przekazać `CWindow` obiekt do żadnej funkcji, która wymaga dojścia do okna. Można łatwo łączyć `CWindow` wywołania metod i wywołania funkcji Win32, bez konieczności tworzenia żadnych obiektów tymczasowych.  
  
 Ponieważ `CWindow` ma składową danych tylko dwa (uchwyt okna i wymiary domyślne), nie nakłada obciążenie na jej kodzie. Ponadto wiele `CWindow` po prostu owijają odpowiedniej funkcji Win32 API. Za pomocą `CWindow`, elementu członkowskiego HWND jest automatycznie przekazywana do funkcji Win32.  
  
 Oprócz używania `CWindow` bezpośrednio, użytkownik może również pochodzić z go, aby dodać dane lub kod do klasy. ATL, sama dziedziczy trzy klasy z `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), i [CContainedWindowT](../atl/using-contained-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

