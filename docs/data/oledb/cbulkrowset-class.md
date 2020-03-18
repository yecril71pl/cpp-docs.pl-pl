---
title: CBulkRowset — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: a235a38531141f306b33093ac2546ae232830f0e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446055"
---
# <a name="cbulkrowset-class"></a>CBulkRowset — Klasa

Pobiera i manipulowanie wierszami w celu pracy z danymi zbiorczo przez pobranie wielu dojść do wierszy z pojedynczym wywołaniem.

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Klasa akcesora.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AddRefRows](#addrefrows)|Zwiększa liczbę odwołań.|
|[CBulkRowset](#cbulkrowset)|Konstruktor.|
|[MoveFirst](#movefirst)|Pobiera pierwszy wiersz danych, wykonując nowe pobieranie zbiorcze w razie potrzeby.|
|[MoveLast](#movelast)|Przenosi do ostatniego wiersza.|
|[Element](#movenext)|Pobiera następny wiersz danych.|
|[MovePrev](#moveprev)|Przenosi do poprzedniego wiersza.|
|[MoveToBookmark](#movetobookmark)|Pobiera wiersz oznaczony zakładką lub wiersz w określonym przesunięciu od tej zakładki.|
|[MoveToRatio](#movetoratio)|Pobiera wiersze zaczynające się od pozycji ułamkowej w zestawie wierszy.|
|[ReleaseRows](#releaserows)|Ustawia bieżący wiersz (`m_nCurrentRow`) na zero i zwalnia wszystkie wiersze.|
|[Setrows](#setrows)|Ustawia liczbę dojść wierszy do pobrania przez jedno wywołanie.|

## <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie klasy `CBulkRowset`.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="addrefrows"></a>CBulkRowset:: AddRefRows

Wywołuje [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) , aby zwiększyć liczbę odwołań dla wszystkich wierszy aktualnie pobieranych z zestawu wierszy bulk.

### <a name="syntax"></a>Składnia

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="cbulkrowset"></a>CBulkRowset:: CBulkRowset

Tworzy nowy obiekt `CBulkRowset` i ustawia domyślną liczbę wierszy na 10.

### <a name="syntax"></a>Składnia

```cpp
CBulkRowset();
```

## <a name="movefirst"></a>CBulkRowset:: MoveFirst

Pobiera pierwszy wiersz danych.

### <a name="syntax"></a>Składnia

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="movelast"></a>CBulkRowset:: MoveLast

Przenosi do ostatniego wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="movenext"></a>CBulkRowset:: MoveNext

Pobiera następny wiersz danych.

### <a name="syntax"></a>Składnia

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. Po osiągnięciu końca zestawu wierszy zwraca DB_S_ENDOFROWSET.

## <a name="moveprev"></a>CBulkRowset:: MovePrev

Przenosi do poprzedniego wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="movetobookmark"></a>CBulkRowset:: MoveToBookmark

Pobiera wiersz oznaczony zakładką lub wiersz w określonym przesunięciu (*lSkip*) z tej zakładki.

### <a name="syntax"></a>Składnia

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Parametry

*Zakładka*<br/>
podczas Zakładka oznaczająca lokalizację, z której mają zostać pobrane dane.

*lSkip*<br/>
podczas Liczba wierszy z zakładki do wiersza docelowego. Jeśli *lSkip* ma wartość zero, pierwszy wiersz jest pobierany z zakładką. Jeśli *lSkip* ma wartość 1, pierwszy wiersz jest pobierany wiersz po wierszu oznaczonym zakładką. Jeśli *lSkip* ma wartość-1, pierwszy wiersz pobierany jest wiersz przed wierszem oznaczonym zakładką.

### <a name="return-value"></a>Wartość zwracana

Zobacz [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="movetoratio"></a>CBulkRowset:: MoveToRatio

Pobiera wiersze zaczynające się od pozycji ułamkowej w zestawie wierszy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Parametry

*nNumerator*<br/>
podczas Licznik używany do określenia pozycji ułamkowej, z której mają zostać pobrane dane.

*nDenominator*<br/>
podczas Mianownik używany do określenia położenia ułamkowego, z którego mają zostać pobrane dane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`MoveToRatio` pobiera wiersze w sposób niezależny od następującej formuły:

`(nNumerator *  RowsetSize ) / nDenominator`

Gdzie `RowsetSize` jest rozmiar zestawu wierszy, mierzony w wierszach. Dokładność tej formuły zależy od konkretnego dostawcy. Aby uzyskać szczegółowe informacje, zobacz [IRowsetScroll:: GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="releaserows"></a>CBulkRowset:: ReleaseRows

Wywołuje [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) , aby zmniejszyć liczbę odwołań dla wszystkich wierszy aktualnie pobranych z zestawu wierszy bulk.

### <a name="syntax"></a>Składnia

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="setrows"></a>CBulkRowset:: setrows

Ustawia liczbę dojść do wierszy pobieranych przez każde wywołanie.

### <a name="syntax"></a>Składnia

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Parametry

*nRows*<br/>
podczas Nowy rozmiar zestawu wierszy (liczba wierszy).

### <a name="remarks"></a>Uwagi

Jeśli wywołasz tę funkcję, musi ona być przed otwarciem zestawu wierszy.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)