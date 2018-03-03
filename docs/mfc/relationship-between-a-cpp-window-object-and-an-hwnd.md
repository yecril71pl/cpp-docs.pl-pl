---
title: "Relacja między obiektem okna języka C++ a właściwością HWND | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HWND
dev_langs:
- C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b441077de3a81de569627b6d7acf7cee8ca17b33
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relacja między obiektem okna języka C++ a właściwością HWND
Okno *obiektu* jest obiektem C++ `CWnd` klasy (lub klasy pochodnej) tworzącą bezpośrednio w programie. Zawiera, a odpowiedź na wywołania programu Konstruktor i destruktor jest częścią. Windows *okna*, z drugiej strony, jest nieprzezroczystego uchwyt do wewnętrzna struktura danych systemu Windows, która odpowiada okna i wykorzystuje zasoby systemowe, jeśli jest obecny. Okno systemu Windows jest identyfikowany przez "uchwytu okna" (`HWND`) i zostanie utworzony po `CWnd` obiekt jest tworzony przez wywołanie do **Utwórz** funkcji członkowskiej klasy `CWnd`. Okno może zostać zniszczone przez wywołanie program lub akcji użytkownika. Uchwyt okna jest przechowywana w obiekcie okna `m_hWnd` zmiennej członkowskiej. Na poniższej ilustracji przedstawiono relacje między obiektem okna języka C++ i okna systemu Windows. Tworzenie okien omówione w [tworzenie Windows](../mfc/creating-windows.md). Niszczenie okien omówione w [niszczenie obiektów okien](../mfc/destroying-window-objects.md).  
  
 ![CWnd obiekt window i okna wynikowego](../mfc/media/vc37fj1.gif "vc37fj1")  
Obiekt Window i okno systemu Windows  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

