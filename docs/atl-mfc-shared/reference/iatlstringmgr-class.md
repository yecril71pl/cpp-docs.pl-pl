---
title: Klasa IAtlStringMgr
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
ms.openlocfilehash: a617ba829999e9e5778bd7f0091cfb0d624dce71
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832012"
---
# <a name="iatlstringmgr-class"></a>Klasa IAtlStringMgr

Ta klasa reprezentuje interfejs `CStringT` Menedżera pamięci.

## <a name="syntax"></a>Składnia

```
__interface IAtlStringMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[Alokacji](#allocate)|Wywołaj tę metodę, aby przydzielić nową strukturę danych ciągu.|
|[Klonowanie](#clone)|Wywołaj tę metodę, aby zwrócić wskaźnik do nowego menedżera ciągów do użycia z innym wystąpieniem `CSimpleStringT` .|
|[Bezpłatna](#free)|Wywołaj tę metodę, aby zwolnić strukturę danych ciągu.|
|[GetNilString](#getnilstring)|Zwraca wskaźnik do `CStringData` obiektu używanego przez puste obiekty ciągu.|
|[Ponowne przydzielenie](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić strukturę danych ciągu.|

## <a name="remarks"></a>Uwagi

Ten interfejs zarządza pamięcią używaną przez klasy ciągów niezależnych od MFC; takie jak [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)i [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Można również użyć tej klasy do zaimplementowania niestandardowego menedżera pamięci dla niestandardowej klasy ciągów. Aby uzyskać więcej informacji, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr. h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a> IAtlStringMgr:: Allocate

Przypisuje nową strukturę danych ciągu.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*nAllocLength*<br/>
Liczba znaków w nowym bloku pamięci.

*nCharSize*<br/>
Rozmiar (w bajtach) typu znaku używanego przez Menedżera ciągów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do nowo przydzielony blok pamięci.

> [!NOTE]
> Nie należy sygnalizować nieudanej alokacji przez wyrzucanie wyjątku. Zamiast tego niepowodzenie alokacji powinno być sygnalizowane przez zwrócenie wartości NULL.

### <a name="remarks"></a>Uwagi

Wywołanie [IAtlStringMgr:: Free](#free) lub [IAtlStringMgr:: Reallocate](#reallocate) w celu zwolnienia pamięci przydzielonej przez tę metodę.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a> IAtlStringMgr:: Clone

Zwraca wskaźnik do nowego menedżera ciągów do użycia z innym wystąpieniem `CSimpleStringT` .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię `IAtlStringMgr` obiektu.

### <a name="remarks"></a>Uwagi

Zwykle wywoływane przez platformę, gdy wymagany jest Menedżer ciągów dla nowego ciągu. W większości przypadków **`this`** zwracany jest wskaźnik.

Jeśli jednak Menedżer pamięci nie obsługuje użycia przez wiele wystąpień `CSimpleStringT` , należy zwrócić wskaźnik do możliwego do współdzielenia Menedżera ciągów.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a> IAtlStringMgr:: Free

Zwalnia strukturę danych ciągu.

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Wskaźnik do bloku pamięci, który ma zostać zwolniony.

### <a name="remarks"></a>Uwagi

Zwalnia określony blok pamięci, który został wcześniej przydzielony po [przydzieleniu lub](#allocate) ponownym [przydzieleniu](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a> IAtlStringMgr::GetNilString

Zwraca wskaźnik do struktury danych ciągu dla pustego ciągu.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CStringData` obiektu używany do reprezentowania pustego ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić reprezentację pustego ciągu.

> [!NOTE]
> Podczas implementowania niestandardowego menedżera ciągów ta funkcja nie może kończyć się niepowodzeniem. Można to zapewnić, osadzając wystąpienie elementu `CNilStringData` w klasie Menedżera ciągów i zwracają wskaźnik do tego wystąpienia.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a> IAtlStringMgr:: Reallocate

Ponownie przydziela strukturę danych ciągu.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci.

*nAllocLength*<br/>
Liczba znaków w nowym bloku pamięci.

*nCharSize*<br/>
Rozmiar (w bajtach) typu znaku używanego przez Menedżera ciągów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielony blok pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zmienić rozmiar istniejącego bloku pamięci określonego przez *pData*.

Wywołaj [IAtlStringMgr:: Free](#free) , aby zwolnić pamięć przydzieloną przez tę metodę.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
