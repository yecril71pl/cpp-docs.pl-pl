---
title: CArrayRowset — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
ms.openlocfilehash: c5f12afa09bc1c62d3287bab93159e217721906f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843251"
---
# <a name="carrayrowset-class"></a>CArrayRowset — Klasa

Uzyskuje dostęp do elementów zestawu wierszy przy użyciu składni tablicy.

## <a name="syntax"></a>Składnia

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>,
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Typ klasy akcesora, która ma być używana przez zestaw wierszy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|--|--|
| [CArrayRowset](#carrayrowset) | Konstruktor. |
| [Snapshot](#snapshot) | Odczytuje cały zestaw wierszy do pamięci. |

### <a name="operators"></a>Operatory

| Nazwa | Opis |
|--|--|
| [&#91;&#93;operatora ](#operator) | Uzyskuje dostęp do elementu zestawu wierszy. |

### <a name="data-members"></a>Elementy członkowskie danych

| Nazwa | Opis |
|--|--|
| [CArrayRowset::m_nRowsRead](#nrowsread) | Liczba wierszy, które zostały już odczytane. |

## <a name="carrayrowsetcarrayrowset"></a><a name="carrayrowset"></a> CArrayRowset:: CArrayRowset

Tworzy nowy `CArrayRowset` obiekt.

### <a name="syntax"></a>Składnia

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Parametry

*Nmaks.*<br/>
podczas Maksymalna liczba wierszy w zestawie wierszy.

## <a name="carrayrowsetsnapshot"></a><a name="snapshot"></a> CArrayRowset:: Snapshot

Odczytuje cały zestaw wierszy do pamięci, tworząc obraz lub migawkę.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Snapshot() throw();
```

## <a name="carrayrowsetoperator"></a><a name="operator"></a> CArrayRowset:: operator

Zapewnia składnię podobną do tablicową do uzyskiwania dostępu do wiersza w zestawie wierszy.

### <a name="syntax"></a>Składnia

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Parametr z szablonem, który określa typ metody dostępu przechowywanej w zestawie wierszy.

*nRow*<br/>
podczas Numer wiersza (elementu tablicy), do którego chcesz uzyskać dostęp.

### <a name="return-value"></a>Wartość zwracana

Zawartość żądanego wiersza.

### <a name="remarks"></a>Uwagi

Jeśli *nrow* przekracza liczbę wierszy w zestawie wierszy, zgłaszany jest wyjątek.

## <a name="carrayrowsetm_nrowsread"></a><a name="nrowsread"></a> CArrayRowset:: m_nRowsRead

Zawiera liczbę wierszy w zestawie wierszy, które zostały już odczytane.

### <a name="syntax"></a>Składnia

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Klasa CRowset](../../data/oledb/crowset-class.md)
