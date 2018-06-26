---
title: Relacja między obiektem okna języka C++ a właściwością HWND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3864de8b3133fd2284b3ce57b75b30d8f41c26a7
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928531"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relacja między obiektem okna języka C++ a właściwością HWND
Okno *obiektu* jest obiektem C++ `CWnd` klasy (lub klasy pochodnej) tworzącą bezpośrednio w programie. Zawiera, a odpowiedź na wywołania programu Konstruktor i destruktor jest częścią. Windows *okna*, z drugiej strony, jest nieprzezroczystego uchwyt do wewnętrzna struktura danych systemu Windows, która odpowiada okna i wykorzystuje zasoby systemowe, jeśli jest obecny. Okno systemu Windows jest identyfikowany przez "uchwytu okna" (`HWND`) i zostanie utworzony po `CWnd` obiekt jest tworzony przez wywołanie do `Create` funkcji członkowskiej klasy `CWnd`. Okno może zostać zniszczone przez wywołanie program lub akcji użytkownika. Uchwyt okna jest przechowywana w obiekcie okna *m_hWnd* zmiennej członkowskiej. Na poniższej ilustracji przedstawiono relacje między obiektem okna języka C++ i okna systemu Windows. Tworzenie okien omówione w [tworzenie Windows](../mfc/creating-windows.md). Niszczenie okien omówione w [niszczenie obiektów okien](../mfc/destroying-window-objects.md).  
  
 ![CWnd obiekt window i okna wynikowego](../mfc/media/vc37fj1.gif "vc37fj1")  
Obiekt Window i okno systemu Windows  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

