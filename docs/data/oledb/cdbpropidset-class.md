---
title: CDBPropIDSet — Klasa
ms.date: 11/04/2016
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
ms.openlocfilehash: e2fced2ed0e32af15e75c7290733fdc2b4b34dc9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447455"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet — Klasa

Dziedziczy z struktury `DBPROPIDSET` i dodaje konstruktora, który inicjuje pola klucza oraz metodę dostępu [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) .

## <a name="syntax"></a>Składnia

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Dodaje właściwość do zestawu identyfikatora właściwości.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor.|
|[SetGUID](#setguid)|Ustawia identyfikator GUID ustawionego identyfikatora właściwości.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_equal)|Przypisuje zawartość jednego identyfikatora właściwości jako inny.|

## <a name="remarks"></a>Uwagi

OLE DB konsumenci używają struktur `DBPROPIDSET`, aby przekazywać tablicę identyfikatorów właściwości, dla których odbiorca chce uzyskać informacje o właściwościach. Właściwości identyfikowane w pojedynczej strukturze [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) należy do jednego zestawu właściwości.

## <a name="addpropertyid"></a>CDBPropIDSet:: AddPropertyID

Dodaje identyfikator właściwości do zestawu identyfikatora właściwości.

### <a name="syntax"></a>Składnia

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parametry

*identyfikatora właściwości*<br/>
podczas Identyfikator właściwości, która ma zostać dodana do zestawu identyfikatora właściwości.

## <a name="cdbpropidset"></a>CDBPropIDSet:: CDBPropIDSet

Konstruktor. Inicjuje `rgProperties`, `cProperties`i (opcjonalnie) `guidPropertySet` pól struktury [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="syntax"></a>Składnia

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID służący do inicjowania pola `guidPropertySet`.

*propidset*<br/>
podczas Inny obiekt `CDBPropIDSet` na potrzeby konstruowania kopii.

## <a name="setguid"></a>CDBPropIDSet:: SetGuid

Ustawia pole GUID w strukturze `DBPROPIDSET`.

### <a name="syntax"></a>Składnia

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID służący do ustawiania pola `guidPropertySet` struktury [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="remarks"></a>Uwagi

To pole można również ustawić przez [konstruktora](../../data/oledb/cdbpropidset-cdbpropidset.md) . Wywołaj tę funkcję, jeśli używasz domyślnego konstruktora dla tej klasy.

## <a name="op_equal"></a>CDBPropIDSet:: operator =

Przypisuje zawartość jednego identyfikatora właściwości ustawionego na inny identyfikator właściwości.

### <a name="syntax"></a>Składnia

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)