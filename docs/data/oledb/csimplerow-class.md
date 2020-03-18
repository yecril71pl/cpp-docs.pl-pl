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
ms.openlocfilehash: 00d8164425ada573020971f66312b2282cc72c45
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441139"
---
# <a name="csimplerow-class"></a>CSimpleRow — Klasa

Udostępnia implementację domyślną dla uchwytu wiersza, który jest używany w klasie [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) .

## <a name="syntax"></a>Składnia

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AddRefRow](#addrefrow)|Dodaje liczbę odwołań do istniejącego dojścia do wiersza.|
|[Compare](#compare)|Porównuje dwa wiersze, aby zobaczyć, czy odwołują się do tego samego wystąpienia wiersza.|
|[CSimpleRow](#csimplerow)|Konstruktor.|
|[ReleaseRow](#releaserow)|Zwalnia wiersze.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_dwRef](#dwref)|Liczba odwołań do istniejącego dojścia do wiersza.|
|[m_iRowset](#irowset)|Indeks zestawu wierszy reprezentujący kursor.|

## <a name="remarks"></a>Uwagi

Dojście do wiersza jest logicznie unikatowym tagiem dla wiersza wynikowego. `IRowsetImpl` tworzy nowy `CSimpleRow` dla każdego wiersza, który zażądał [IRowsetImpl:: GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` można również zastąpić własną implementacją uchwytu wiersza, ponieważ jest to domyślny argument szablonu do `IRowsetImpl`. Jedynym wymaganiem do zamiany tej klasy jest posiadanie konstruktora, który akceptuje pojedynczy parametr typu **Long**.

## <a name="addrefrow"></a>CSimpleRow:: AddRefRow

Dodaje liczbę odwołań do istniejącego uchwytu wiersza w sposób bezpieczny dla wątków.

### <a name="syntax"></a>Składnia

```cpp
DWORD AddRefRow();
```

## <a name="compare"></a>CSimpleRow:: Compare

Porównuje dwa wiersze, aby zobaczyć, czy odwołują się do tego samego wystąpienia wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Parametry

*pRow*<br/>
Wskaźnik do obiektu `CSimpleRow`.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT, zwykle S_OK, wskazującą dwa wiersze, jest tym samym wystąpieniem wiersza lub S_FALSE, co oznacza, że dwa wiersze są różne. Aby uzyskać inne możliwe wartości zwracane, zobacz [IRowsetIdentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) w *dokumentacji programisty OLE DB* .

## <a name="csimplerow"></a>CSimpleRow:: CSimpleRow

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Parametry

*iRowsetCur*<br/>
podczas Indeks do bieżącego zestawu wierszy.

### <a name="remarks"></a>Uwagi

Ustawia [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) na *iRowsetCur*.

## <a name="releaserow"></a>CSimpleRow:: ReleaseRow

Zwalnia wiersze w sposób bezpieczny dla wątków.

### <a name="syntax"></a>Składnia

```cpp
DWORD ReleaseRow();
```

## <a name="dwref"></a>CSimpleRow:: m_dwRef

Liczba odwołań do istniejącego dojścia do wiersza.

### <a name="syntax"></a>Składnia

```cpp
DWORD m_dwRef;
```

## <a name="irowset"></a>CSimpleRow:: m_iRowset

Indeks zestawu wierszy reprezentujący kursor.

### <a name="syntax"></a>Składnia

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl, klasa](../../data/oledb/irowsetimpl-class.md)