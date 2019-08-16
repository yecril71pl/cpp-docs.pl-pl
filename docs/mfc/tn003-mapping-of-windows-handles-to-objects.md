---
title: 'TN003: Mapowanie dojść systemu Windows do obiektów'
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 45492963e1b686e03eb59c320fdc3d52d1534f7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513541"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003: Mapowanie dojść systemu Windows do obiektów

Ta Uwaga opisuje procedury MFC, które obsługują mapowanie uchwytów obiektów systemu Windows C++ do obiektów.

## <a name="the-problem"></a>Problem

Obiekty systemu Windows są zwykle reprezentowane przez [](/windows/win32/WinProg/windows-data-types) różne obiekty uchwytu klasy MFC zawijają uchwyty obiektów C++ systemu Windows z obiektami. Funkcja zawijania uchwytów biblioteki klas MFC umożliwia znalezienie C++ obiektu, który otacza obiekt systemu Windows, który ma określony uchwyt. Jednak czasami obiekt nie ma obiektu C++ otoki i w tym momencie system tworzy tymczasowy obiekt do działania jako C++ otoka.

Obiekty systemu Windows korzystające z map obsługi są następujące:

- HWND ([CWnd](../mfc/reference/cwnd-class.md) i `CWnd`-pochodne klasy)

- Używający HDC ([](../mfc/reference/cdc-class.md) wyskakujące i `CDC`pochodne klasy)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([Korzystanie CImageList](../mfc/reference/cimagelist-class.md))

- GNIAZDO ([CSocket](../mfc/reference/csocket-class.md))

Uwzględniając dojście do dowolnego z tych obiektów, można znaleźć obiekt MFC, który zawija uchwyt poprzez wywołanie metody `FromHandle`statycznej. Na przykład, mając Właściwość HWND o nazwie *HWND*, poniższy wiersz zwróci wskaźnik do obiektu, który `CWnd` zawija wartość *HWND*:

```
CWnd::FromHandle(hWnd)
```

Jeśli *Właściwość HWND* nie ma określonego obiektu otoki, jest tworzona `CWnd` tymczasowa, aby otoczyć *Właściwość HWND*. Dzięki temu można uzyskać prawidłowy C++ obiekt z dowolnego dojścia.

Po utworzeniu obiektu otoki można pobrać jego uchwyt z publicznej zmiennej składowej klasy otoki. W przypadku elementu `CWnd`, *m_hWnd* zawiera właściwość HWND dla tego obiektu.

## <a name="attaching-handles-to-mfc-objects"></a>Dołączanie dojść do obiektów MFC

W przypadku nowo utworzonego obiektu otoki uchwytu i dojścia do obiektu systemu Windows można skojarzyć te dwa, wywołując `Attach` funkcję w tym przykładzie:

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

Oznacza to, że wpis w trwałej mapie kojarzy *myWnd* i *HWND*. Wywołanie `CWnd::FromHandle(hWnd)` zwróci teraz wskaźnik do *myWnd*. Po usunięciu *myWnd* , destruktor automatycznie niszczy *Właściwość HWND* przez wywołanie funkcji [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow) systemu Windows. Jeśli nie jest to wymagane, *Właściwość HWND* musi być odłączona od *myWnd* przed zniszczeniem *myWnd* (zwykle przy opuszczaniu zakresu, w którym zdefiniowano *myWnd* ). Ta `Detach` Metoda.

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>Więcej informacji o obiektach tymczasowych

Obiekty tymczasowe są tworzone za `FromHandle` każdym razem, gdy zostanie dostarczone dojście, które nie ma jeszcze obiektu otoki. Te obiekty tymczasowe są odłączone od ich uchwytu i usuwane przez `DeleteTempMap` funkcje. Domyślnie [CWinThread:: OnIdle](../mfc/reference/cwinthread-class.md#onidle) automatycznie wywołuje `DeleteTempMap` dla każdej klasy, która obsługuje mapy uchwytów tymczasowych. Oznacza to, że nie można założyć, że wskaźnik do obiektu tymczasowego będzie prawidłowy poza punktem wyjścia z funkcji, w której uzyskano wskaźnik.

## <a name="wrapper-objects-and-multiple-threads"></a>Obiekty otoki i wiele wątków

Zarówno obiekt tymczasowy, jak i trwały są utrzymywane dla każdego wątku. Oznacza to, że jeden wątek nie może uzyskać dostępu C++ do obiektów otoki innego wątku, niezależnie od tego, czy jest on tymczasowy, czy trwały.

Aby przekazać te obiekty z jednego wątku do innego, należy zawsze wysyłać je jako ich `HANDLE` typy natywne. Przekazanie C++ obiektu otoki z jednego wątku do innego często spowoduje nieoczekiwane wyniki.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
