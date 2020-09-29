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
ms.openlocfilehash: 4de218188326dad434c5b0d355a3a15d39bb576c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502503"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet — Klasa

Dziedziczy ze `DBPROPIDSET` struktury i dodaje konstruktora, który inicjuje pola klucza oraz metodę dostępu [AddPropertyID](#addpropertyid) .

## <a name="syntax"></a>Składnia

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[AddPropertyID](#addpropertyid)|Dodaje właściwość do zestawu identyfikatora właściwości.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor.|
|[SetGUID](#setguid)|Ustawia identyfikator GUID ustawionego identyfikatora właściwości.|

### <a name="operators"></a>Operatory

| Nazwa | Opis |
|-|-|
|[operator =](#op_equal)|Przypisuje zawartość jednego identyfikatora właściwości jako inny.|

## <a name="remarks"></a>Uwagi

OLE DB konsumenci używają `DBPROPIDSET` struktur do przekazywania tablicy identyfikatorów właściwości, dla których odbiorca chce uzyskać informacje o właściwościach. Właściwości identyfikowane w pojedynczej strukturze [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) należy do jednego zestawu właściwości.

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a> CDBPropIDSet:: AddPropertyID

Dodaje identyfikator właściwości do zestawu identyfikatora właściwości.

### <a name="syntax"></a>Składnia

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parametry

*identyfikatora właściwości*<br/>
podczas Identyfikator właściwości, która ma zostać dodana do zestawu identyfikatora właściwości.

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a> CDBPropIDSet:: CDBPropIDSet

Konstruktor. Inicjuje `rgProperties` pola, `cProperties` , i (opcjonalnie) `guidPropertySet` struktury [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="syntax"></a>Składnia

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parametry

*guid*<br/>
podczas Identyfikator GUID służący do inicjowania `guidPropertySet` pola.

*propidset*<br/>
podczas Inny `CDBPropIDSet` obiekt dla konstruowania kopii.

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a> CDBPropIDSet:: SetGuid

Ustawia pole GUID w `DBPROPIDSET` strukturze.

### <a name="syntax"></a>Składnia

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*guid*<br/>
podczas Identyfikator GUID służący do ustawiania `guidPropertySet` pola struktury [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="remarks"></a>Uwagi

To pole można również ustawić przez [konstruktora](#cdbpropidset) . Wywołaj tę funkcję, jeśli używasz domyślnego konstruktora dla tej klasy.

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a> CDBPropIDSet:: operator =

Przypisuje zawartość jednego identyfikatora właściwości ustawionego na inny identyfikator właściwości.

### <a name="syntax"></a>Składnia

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
