---
title: IAtlStringMgr, klasa
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: 978d33c719b9cb8c2708dc97fa78874534dfd748
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749961"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr, klasa

Ta klasa reprezentuje interfejs służący do `CStringT` Menedżer pamięci.

## <a name="syntax"></a>Składnia

```
__interface IAtlStringMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Przydziel](#allocate)|Wywołaj tę metodę można przydzielić nowej struktury danych ciągu.|
|[Clone](#clone)|Wywołaj tę metodę, aby zwrócić wskaźnik do nowego Menedżera ciąg do użycia z innego wystąpienia programu `CSimpleStringT`.|
|[Bezpłatna](#free)|Wywołaj tę metodę, aby zwolnić struktury danych ciągu.|
|[GetNilString](#getnilstring)|Zwraca wskaźnik do `CStringData` obiekt używany przez obiekty pusty ciąg.|
|[Ponowne przydzielenie](#reallocate)|Wywołaj tę metodę w celu ponownego przydzielenia struktury danych ciągu.|

## <a name="remarks"></a>Uwagi

Ten interfejs zarządza pamięci używane przez klasy ciągu niezależne od MFC; takie jak [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), i [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Ta klasa umożliwia również zaimplementować Menedżera pamięci niestandardowe dla swojej klasy niestandardowy ciąg. Aby uzyskać więcej informacji, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

##  <a name="allocate"></a>  IAtlStringMgr::Allocate

Przydziela nową strukturę danych ciągu.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*nAllocLength*<br/>
Liczba znaków w nowy blok pamięci.

*nCharSize*<br/>
Rozmiar (w bajtach) to typ znaku używany przez Menedżera ciągów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bloku pamięci nowo przydzielone.

> [!NOTE]
>  Sygnalizuje błąd alokacji, zostanie zgłoszony wyjątek. Zamiast tego błąd alokacji powinny być zasygnalizowany, zwracając wartość NULL.

### <a name="remarks"></a>Uwagi

Wywołaj [IAtlStringMgr::Free](#free) lub [IAtlStringMgr::ReAllocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.

> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="clone"></a>  IAtlStringMgr::Clone

Zwraca wskaźnik do nowego Menedżera ciąg do użycia z innego wystąpienia programu `CSimpleStringT`.

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię obiektu `IAtlStringMgr` obiektu.

### <a name="remarks"></a>Uwagi

Często wywoływane przez platformę, gdy Menedżera ciągów jest wymagany w przypadku nowego ciągu. W większości przypadków **to** wskaźnik jest zwracany.

Jednak jeśli Menedżer pamięci nie obsługuje on używany przez wiele wystąpień `CSimpleStringT`, wskaźnik do Menedżera zabezpieczać ciągu ma zostać zwrócony.

> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="free"></a>  IAtlStringMgr::Free

Zwalnia struktury danych ciągu.

```
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Wskaźnik do bloku pamięci, który ma zostać zwolniony.

### <a name="remarks"></a>Uwagi

Zwalnia blok pamięci określonej uprzednio przydzielonej przez [przydziel](#allocate) lub [ponowne przydzielenie](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="getnilstring"></a>  IAtlStringMgr::GetNilString

Zwraca wskaźnik do struktury danych ciągu dla pustego ciągu.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CStringData` obiekt używany do reprezentowania pusty ciąg.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić reprezentację pusty ciąg.

> [!NOTE]
> Podczas implementowania Menedżera niestandardowy ciąg, ta funkcja nigdy nie musi się niepowodzeniem. Może to zapewnić, osadzając wystąpienie `CNilStringData` w ciągu Menedżera klasy i powrót wskaźnika do tego wystąpienia.

> [!NOTE]
> Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="reallocate"></a>  IAtlStringMgr::Reallocate

Przydzieli struktury danych ciągu.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.

*nAllocLength*<br/>
Liczba znaków w nowy blok pamięci.

*nCharSize*<br/>
Rozmiar (w bajtach) to typ znaku używany przez Menedżera ciągów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku bloku nowo alokacji pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zmienić rozmiar istniejącej bloku pamięci określonej przez *pData*.

Wywołaj [IAtlStringMgr::Free](#free) zwolnienie pamięci przydzielonej przez tę metodę.

> [!NOTE]
> Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
