---
title: 'TN003: Mapowanie Windows uchwytów na obiekty'
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: e7844398ebaf5a8fdf8c56ab18b33d8c7717d1ad
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326702"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003: Mapowanie Windows uchwytów na obiekty

Ta uwaga opisuje MFC procedur, które obsługuje mapowania Windows obiektu dojścia do obiektów języka C++.

## <a name="the-problem"></a>Ten Problem

Obiekty Windows zwykle są reprezentowane przez różne [obsługi](/windows/desktop/WinProg/windows-data-types) obiektów klas MFC opakować Windows uchwytów obiektu z obiektami C++. Uchwyt otaczania funkcji biblioteki klas MFC pozwalają znaleźć obiektu języka C++, do którego jest zawijany obiekt Windows, który ma określoną dojście. Jednak czasami obiekt nie ma obiektu języka C++ i w tych godzinach system tworzy tymczasowy obiekt jako otoki języka C++.

Windows obiektów, które uchwyt mapy są następujące:

- HWND ([CWnd](../mfc/reference/cwnd-class.md) i `CWnd`-klas pochodnych)

- Elementu HDC ([CDC](../mfc/reference/cdc-class.md) i `CDC`-klas pochodnych)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- Hpen — ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- GNIAZDA ([CSocket](../mfc/reference/csocket-class.md))

Podane dojście do jednej z tych obiektów, można znaleźć obiektu MFC, który otacza uchwytu przez wywołanie metody statycznej `FromHandle`. Na przykład, biorąc pod uwagę HWND o nazwie *hWnd*, zwraca wskaźnik do następujący wiersz `CWnd` to opakowuje *hWnd*:

```
CWnd::FromHandle(hWnd)
```

Jeśli *hWnd* nie ma określonego obiektu, to tymczasowy `CWnd` zostanie utworzony, aby zawijać *hWnd*. Dzięki temu można uzyskać prawidłowego obiektu języka C++ z dowolnego uchwytu.

Po utworzeniu obiektu, można pobrać uchwytu ze zmiennej publicznej składowej klasy otoki. W przypadku właściwości `CWnd`, *m_hWnd* zawiera HWND dla tego obiektu.

## <a name="attaching-handles-to-mfc-objects"></a>Dołączanie dojścia do obiektów MFC

Biorąc pod uwagę nowo utworzony dojście-obiektu i jego uchwyt do obiektu Windows, należy skojarzyć dwóch przez wywołanie metody `Attach` działa jak w poniższym przykładzie:

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

To sprawia, że wpis w kojarzenie stałe mapy *myWnd* i *hWnd*. Wywoływanie `CWnd::FromHandle(hWnd)` teraz zwraca wskaźnik do *myWnd*. Gdy *myWnd* jest usunięte, destruktor automatycznie zniszcz *hWnd* wywołując Windows [destroywindow —](/windows/desktop/api/winuser/nf-winuser-destroywindow) funkcji. Jeśli jest to niepożądane, *hWnd* musi zostać odłączony od *myWnd* przed *myWnd* zostanie zniszczony (zwykle w przypadku, gdy opuszczania zakresu, w którym *myWnd*została zdefiniowana). `Detach` To realizowane przez metodę.

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>Więcej informacji na temat obiektów tymczasowych.

Obiekty tymczasowe są tworzone po każdym `FromHandle` otrzymuje uchwyt, który nie ma już obiekt otoki. Takie obiekty tymczasowe są odłączone od ich dojścia i usunięte przez `DeleteTempMap` funkcji. Domyślnie [CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle) automatycznie wywołuje `DeleteTempMap` dla każdej klasy, która obsługuje uchwyt tymczasowego mapy. Oznacza to, że możesz nie zakłada, że wskaźnik do obiektów tymczasowych prawidłowe poza punktem wyjścia z funkcji której uzyskano wskaźnika.

## <a name="wrapper-objects-and-multiple-threads"></a>Otoki obiektów i wiele wątków

Obiekty tymczasowe i stałe są przechowywane na zasadzie na wątek. Oznacza to jeden wątek nie może uzyskać dostęp do obiektów otoki C++ innego wątku, niezależnie od tego, czy jest tymczasowy lub stały.

Aby przekazać te obiekty z jednego wątku do innego, zawsze wysyłać je jako ich native `HANDLE` typu. Przekazywanie obiektu języka C++ z jednego wątku do innego często spowodować nieoczekiwane rezultaty.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
