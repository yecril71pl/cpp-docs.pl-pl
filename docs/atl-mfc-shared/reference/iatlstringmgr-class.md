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
ms.openlocfilehash: 49ef7850edb18cd51092f282644973376abd4c7c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317486"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr, klasa

Ta klasa reprezentuje interfejs `CStringT` do menedżera pamięci.

## <a name="syntax"></a>Składnia

```
__interface IAtlStringMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Przydzielić](#allocate)|Wywołanie tej metody, aby przydzielić nową strukturę danych ciągu.|
|[Klonowanie](#clone)|Wywołanie tej metody, aby zwrócić wskaźnik do nowego `CSimpleStringT`menedżera ciągów do użycia z innym wystąpieniem .|
|[Bezpłatna](#free)|Wywołanie tej metody, aby zwolnić strukturę danych ciągu.|
|[GetNilStrąk](#getnilstring)|Zwraca wskaźnik do `CStringData` obiektu używanego przez puste obiekty ciągu.|
|[Ponowne przydzielić](#reallocate)|Wywołanie tej metody, aby ponownie przydzielić strukturę danych ciągu.|

## <a name="remarks"></a>Uwagi

Ten interfejs zarządza pamięcią używaną przez klasy ciągów niezależne od MFC; takich jak [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)i [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Można również użyć tej klasy do zaimplementowania menedżera pamięci niestandardowej dla niestandardowej klasy ciągu. Aby uzyskać więcej informacji, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr::Przydziel

Przydziela nową strukturę danych ciągu.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*nAllocLength (Niem.*<br/>
Liczba znaków w nowym bloku pamięci.

*nCharSize (Rozmiar)*<br/>
Rozmiar (w bajtach) typu znaku używanego przez menedżera ciągów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do nowo przydzielonego bloku pamięci.

> [!NOTE]
> Nie sygnalizuj alokacji nie powiodło się, zgłaszając wyjątek. Zamiast tego alokacji nie powiodło się powinny być sygnalizowane przez zwrócenie null.

### <a name="remarks"></a>Uwagi

Wywołanie [IAtlStringMgr::Free](#free) lub [IAtlStringMgr::ReAllocate](#reallocate) zwolnić pamięć przydzieloną przez tę metodę.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr::Klon

Zwraca wskaźnik do nowego menedżera ciągów do `CSimpleStringT`użytku z innym wystąpieniem programu .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię `IAtlStringMgr` obiektu.

### <a name="remarks"></a>Uwagi

Powszechnie wywoływane przez strukturę, gdy menedżer ciągów jest potrzebne dla nowego ciągu. W większości przypadków **ten** wskaźnik jest zwracany.

Jednak jeśli menedżer pamięci nie obsługuje używane przez `CSimpleStringT`wiele wystąpień , wskaźnik do menedżera ciągów sharable powinny być zwracane.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr::Wolny

Zwalnia strukturę danych ciągu.

```
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Wskaźnik do bloku pamięci do uwolnienia.

### <a name="remarks"></a>Uwagi

Zwalnia określony blok pamięci wcześniej przydzielony przez [Allocate](#allocate) lub [Reallocate](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringGgr::GetNilString

Zwraca wskaźnik do struktury danych ciągu dla pustego ciągu.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CStringData` obiektu używanego do reprezentowania pustego ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zwrócić reprezentację pustego ciągu.

> [!NOTE]
> Podczas implementowania menedżera ciągów niestandardowych, ta funkcja nigdy nie może zakończyć się niepowodzeniem. Można to zapewnić, osadzając `CNilStringData` wystąpienie w klasie menedżera ciągów i zwracać wskaźnik do tego wystąpienia.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr::Ponowne przydzielenie

Ponownie przydziela strukturę danych ciągu.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci.

*nAllocLength (Niem.*<br/>
Liczba znaków w nowym bloku pamięci.

*nCharSize (Rozmiar)*<br/>
Rozmiar (w bajtach) typu znaku używanego przez menedżera ciągów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielonego bloku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zmienić rozmiar istniejącego bloku pamięci określonego przez *pData*.

Wywołanie [IAtlStringMgr::Free](#free) zwolnić pamięć przydzieloną przez tę metodę.

> [!NOTE]
> Aby zapoznać się z przykładami użycia, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
