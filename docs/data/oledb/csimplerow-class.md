---
title: CSimpleRow — Klasa
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: 19b90f4454e784907366ef6cf7e3e7e1b9ada799
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390935"
---
# <a name="csimplerow-class"></a>CSimpleRow — Klasa

Udostępnia domyślną implementację dla dojście do wiersza, który jest używany w [irowsetimpl —](../../data/oledb/irowsetimpl-class.md) klasy.

## <a name="syntax"></a>Składnia

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Addrefrow —](#addrefrow)|Dodaje licznik odwołań do istniejących uchwyt wiersza.|
|[Compare](#compare)|Porównuje dwa wiersze, aby zobaczyć, jeśli odnoszą się do tego samego wystąpienia wiersza.|
|[CSimpleRow](#csimplerow)|Konstruktor.|
|[Releaserow —](#releaserow)|Wersje wierszy.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_dwRef](#dwref)|Liczba odwołań do istniejących uchwyt wiersza.|
|[m_iRowset](#irowset)|Indeks wierszy reprezentujący kursora.|

## <a name="remarks"></a>Uwagi

Dojście do wiersza jest logicznie unikatowych tagów na podstawie wyniku wiersza. `IRowsetImpl` Tworzy nową `CSimpleRow` dla każdego wiersza w wymagane [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` może zostać również zamienione Twojej własnej implementacji dojście do wiersza, ponieważ jest domyślny argument szablonu, aby `IRowsetImpl`. Jedynym wymaganiem, które można zmienić tej klasy jest Klasa zastępcza dostarczyć konstruktora, który przyjmuje jeden parametr typu **długie**.

## <a name="addrefrow"></a> CSimpleRow::AddRefRow

Dodaje licznik odwołań do istniejących dojściem do wiersza, w sposób bezpieczny dla wątków.

### <a name="syntax"></a>Składnia

```cpp
DWORD AddRefRow();
```

## <a name="compare"></a> CSimpleRow::Compare

Porównuje dwa wiersze, aby zobaczyć, jeśli odnoszą się do tego samego wystąpienia wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Parametry

*pRow*<br/>
Wskaźnik do `CSimpleRow` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT, zwykle S_OK, wskazującą dwa wiersze są tego samego wystąpienia wiersz lub wartość S_FALSE, wskazując dwa wiersze są różne. Zobacz [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) w *OLE DB Podręcznik programisty* dla innych możliwych wartości zwracanych.

## <a name="csimplerow"></a> CSimpleRow::CSimpleRow

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Parametry

*iRowsetCur*<br/>
[in] Indeks bieżącego zestawu wierszy.

### <a name="remarks"></a>Uwagi

Zestawy [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) do *iRowsetCur*.

## <a name="releaserow"></a> CSimpleRow::ReleaseRow

Wersje wierszy w sposób bezpieczny dla wątków.

### <a name="syntax"></a>Składnia

```cpp
DWORD ReleaseRow();
```

## <a name="dwref"></a> CSimpleRow::m_dwRef

Liczba odwołań do istniejących uchwyt wiersza.

### <a name="syntax"></a>Składnia

```cpp
DWORD m_dwRef;
```

## <a name="irowset"></a> CSimpleRow::m_iRowset

Indeks wierszy reprezentujący kursora.

### <a name="syntax"></a>Składnia

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl, klasa](../../data/oledb/irowsetimpl-class.md)