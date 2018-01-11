---
title: "TN003: Mapowanie uchwytów okien na obiekty | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mapping
dev_langs: C++
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e53b2569b0da6bfa63c94adb7bb163e5bcd6b7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003: mapowanie uchwytów okien na obiekty
Ta uwaga opisuje MFC dojścia do obiektów C++ obiekt procedur, które obsługuje mapowania systemu Windows.  
  
## <a name="the-problem"></a>Problem  
 Obiekty systemu Windows są zazwyczaj reprezentowany przez różne [obsługi](http://msdn.microsoft.com/library/windows/desktop/aa383751) obiektów klas MFC zawijać uchwytami systemu Windows z obiektami C++. Dojście zawijania funkcje biblioteki klas MFC umożliwiają znaleźć obiekt C++, który jest zawijany obiektu systemu Windows, który ma określonego dojścia. Jednak czasami obiekt nie ma obiektu C++ i w tych godzinach system tworzy tymczasowy obiekt do działania jako otoki C++.  
  
 Obiektów systemu Windows, które mapy dojścia są następujące:  
  
-   Właściwość HWND ([CWnd](../mfc/reference/cwnd-class.md) i `CWnd`-klas pochodnych)  
  
-   Elementu HDC ([CDC](../mfc/reference/cdc-class.md) i `CDC`-klas pochodnych)  
  
-   HMENU ([cmenu —](../mfc/reference/cmenu-class.md))  
  
-   Hpen — ([CGdiObject](../mfc/reference/cgdiobject-class.md))  
  
-   HBRUSH (`CGdiObject`)  
  
-   HFONT (`CGdiObject`)  
  
-   HBITMAP (`CGdiObject`)  
  
-   HPALETTE (`CGdiObject`)  
  
-   HRGN — (`CGdiObject`)  
  
-   HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))  
  
-   GNIAZDA ([CSocket —](../mfc/reference/csocket-class.md))  
  
 Podane dojście do dowolnego z tych obiektów, można znaleźć obiektu MFC, który opakowuje dojście przez wywołanie metody statycznej `FromHandle`. Na przykład, dla danego HWND o nazwie `hWnd`, zwraca wskaźnik do następującego `CWnd` który opakowuje `hWnd`:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 Jeśli `hWnd` nie ma określonego obiektu, tymczasowej `CWnd` utworzeniu opakowywać `hWnd`. Dzięki temu można uzyskać prawidłowy obiekt C++ z dowolnego uchwytu.  
  
 Po utworzeniu obiektu można pobrać uchwytu zmiennej publicznego elementu członkowskiego klasy otoki. W przypadku liczby `CWnd`, `m_hWnd` zawiera HWND dla tego obiektu.  
  
## <a name="attaching-handles-to-mfc-objects"></a>Dołączanie dojść do obiektów MFC  
 Biorąc pod uwagę nowo utworzony uchwyt-obiektu i dojścia do obiektu systemu Windows, można skojarzyć dwa przez wywołanie metody `Attach` działać jak w poniższym przykładzie:  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);
```  
  
 Dzięki temu podczas kojarzenia stałe mapy wpis `myWnd` i `hWnd`. Wywoływanie `CWnd::FromHandle(hWnd)` teraz zwraca wskaźnik do `myWnd`. Gdy `myWnd` jest usunięte, destruktor automatycznie zniszczy `hWnd` przez wywołanie systemu Windows [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682) funkcji. Jeśli jest to niepożądane, `hWnd` musi zostać odłączony od `myWnd` przed `myWnd` zostanie zniszczony (zwykle, podczas opuszczania zakresu, w którym `myWnd` została zdefiniowana). `Detach` Metody robi to.  
  
```  
myWnd.Detach();
```  
  
## <a name="more-about-temporary-objects"></a>Więcej informacji na temat obiekty tymczasowe  
 Obiekty tymczasowe są tworzone przy każdym `FromHandle` podano uchwytu, które jeszcze nie ma obiektu. Te obiekty tymczasowe są odłączone od ich dojścia i usuwane przez `DeleteTempMap` funkcji. Domyślnie [CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle) automatycznie wywołuje `DeleteTempMap` dla każdej klasy, która obsługuje mapy dojście tymczasowe. Oznacza to, że możesz nie przyjęto założenie, że wskaźnik do tymczasowego obiektu będzie obowiązywać poza punkt wyjścia z funkcji których uzyskano kursor.  
  
## <a name="wrapper-objects-and-multiple-threads"></a>Otoki obiektów i wiele wątków  
 Obiekty zarówno tymczasowe i stałe są obsługiwane na podstawie dla każdego wątku. Oznacza to, że jeden wątek nie może uzyskać dostępu inny wątek C++ otoki obiektów, niezależnie od tego, czy jest tymczasowych lub trwałych.  
  
 Aby przekazać te obiekty z jednego wątku do innego, zawsze wysyłać je jako ich native `HANDLE` typu. Przekazywanie obiektu języka C++ z jednego wątku na inny często spowodować nieoczekiwane wyniki.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

