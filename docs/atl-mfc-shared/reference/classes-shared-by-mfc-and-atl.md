---
title: Klasy współdzielone MFC i ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491462"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Klasy współdzielone MFC i ATL

W poniższej tabeli wymieniono klasy współdzielone między MFC i ATL.

|Class|Opis|Plik nagłówka|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Zapewnia metody zarządzania wartościami daty i godziny skojarzonych z plikiem.|atltime. h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Zapewnia metody zarządzania względnymi wartościami daty i godziny skojarzonych z plikiem.|atltime. h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Reprezentuje obiekt String z buforem o stałym znaku.|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Zapewnia obsługę ulepszonej mapy bitowej, w tym możliwość ładowania i zapisywania obrazów w formatach JPEG, GIF, BMP i Portable Network Graphics (PNG).|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Hermetyzuje typ danych daty używany w automatyzacji OLE.|ATLComTime. h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Reprezentuje czas względny, przedział czasu.|ATLComTime. h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Klasa podobna do struktury [punktu](/windows/win32/api/windef/ns-windef-point) systemu Windows, która zawiera również funkcje elementów członkowskich do `CPoint` manipulowania i `POINT` struktur.|atltypes. h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Klasa podobna do struktury Windows [Rect](/windows/win32/api/windef/ns-windef-rect) , która obejmuje również funkcje elementów członkowskich do manipulowania `CRect` obiektami i strukturami systemu Windows. `RECT`|atltypes. h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|`CSimpleStringT` Reprezentuje obiekt.|atlsimpstr. h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Klasa podobna do struktury [rozmiaru](/windows/win32/api/windef/ns-windef-size) systemu Windows, która implementuje względną współrzędną lub położeniu.|atltypes. h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Umożliwia automatyczne czyszczenie `GetBuffer` zasobów i `ReleaseBuffer` wywoływanie na istniejącym `CStringT` obiekcie.|atlsimpstr. h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Reprezentuje dane obiektu ciągu.|atlsimpstr. h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|`CStringT` Reprezentuje obiekt.|CStringT. h (zależna od MFC) pliku atlstr. h (niezależna od MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Reprezentuje bezwzględną godzinę i datę.|atltime. h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Czas, który jest wewnętrznie przechowywany jako liczba sekund w przedziale czasu.|atltime. h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Reprezentuje interfejs `CStringT` Menedżera pamięci.|atlsimpstr. h|

## <a name="see-also"></a>Zobacz także

[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
