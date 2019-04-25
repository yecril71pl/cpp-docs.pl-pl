---
title: Klasy współdzielone MFC i ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: 5376a87aac2b82615cd48f80e0e95208b8132bf0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235149"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Klasy współdzielone MFC i ATL

W poniższej tabeli wymieniono klasy współdzielone MFC i ATL.

|Class|Opis|Plik nagłówkowy|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Udostępnia metody dla zarządzania skojarzonych z plikiem wartości daty i godziny.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Udostępnia metody dla zarządzania względne wartości daty i godziny skojarzonych z plikiem.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Reprezentuje obiekt ciągu z buforem stałych znaków.|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Zapewnia obsługę rozszerzonych mapy bitowej, łącznie z możliwością ładowania i zapisać obrazy w formacie JPEG, GIF, BMP i przenośnych Network Graphics (PNG).|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Hermetyzuje typ danych daty używany w automatyzacji OLE.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Reprezentuje względne czasu, przedział czasu.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Podobnie jak Windows klasy [punktu](/windows/desktop/api/windef/ns-windef-tagpoint) strukturę, która obejmuje również funkcji elementów członkowskich do manipulowania `CPoint` i `POINT` struktury.|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Podobnie jak Windows klasy [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) strukturę, która obejmuje również funkcji elementów członkowskich do manipulowania `CRect` obiektów i Windows `RECT` struktury.|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Reprezentuje `CSimpleStringT` obiektu.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Podobnie jak Windows klasy [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury, która implementuje współrzędne względne lub pozycję.|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Umożliwia czyszczenie zasobów automatyczne dla `GetBuffer` i `ReleaseBuffer` wywołuje w ramach istniejącego `CStringT` obiektu.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Reprezentuje dane obiektu string.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Reprezentuje `CStringT` obiektu.|pliku atlstr.h cstringt.h (MFC zależnych od ustawień lokalnych) (niezależnie od MFC)|
|[Ctime —](../../atl-mfc-shared/reference/ctime-class.md)|Reprezentuje bezwzględnego czasu i daty.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Ilość czasu, który jest wewnętrznie przechowywana jako liczbę sekund w przedziale czasu.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Reprezentuje interfejs służący do `CStringT` Menedżer pamięci.|atlsimpstr.h|

## <a name="see-also"></a>Zobacz także

[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
