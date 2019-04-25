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
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
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
ms.openlocfilehash: 9e878af3acf4c4d3a6ca785454c4bb072f17cf09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209324"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet — Klasa

Dziedziczy `DBPROPIDSET` struktury i dodaje konstruktora, który inicjuje pola klucza, jak również [addpropertyid —](../../data/oledb/cdbpropidset-addpropertyid.md) dostęp do metody.

## <a name="syntax"></a>Składnia

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Dodaje właściwość do zestawu identyfikator właściwości.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor.|
|[Setguid —](#setguid)|Ustawia ustawiony identyfikator GUID Identyfikatora właściwości.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_equal)|Przypisuje zawartość jednym Identyfikatorem właściwości zestawu do drugiego.|

## <a name="remarks"></a>Uwagi

Użyj konsumentów OLE DB `DBPROPIDSET` struktur, aby przekazać tablicę identyfikatorów właściwości, dla których użytkownik chce uzyskać informacje o właściwościach. Właściwości określone w pojedynczej [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) struktury należą do zestawu jednej właściwości.

## <a name="addpropertyid"></a> CDBPropIDSet::AddPropertyID

Dodaje identyfikator właściwości zestawu identyfikator właściwości.

### <a name="syntax"></a>Składnia

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parametry

*identyfikatora właściwości*<br/>
[in] Ustaw identyfikator właściwości, które mają zostać dodane do Identyfikatora właściwości.

## <a name="cdbpropidset"></a> CDBPropIDSet::CDBPropIDSet

Konstruktor. Inicjuje `rgProperties`, `cProperties`oraz (opcjonalnie) `guidPropertySet` pola [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) struktury.

### <a name="syntax"></a>Składnia

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parametry

*Identyfikator GUID*<br/>
[in] Identyfikator GUID służący do zainicjowania `guidPropertySet` pola.

*propidset*<br/>
[in] Inny `CDBPropIDSet` obiekt do tworzenia kopii.

## <a name="setguid"></a> CDBPropIDSet::SetGUID

Ustawia pole identyfikatora GUID `DBPROPIDSET` struktury.

### <a name="syntax"></a>Składnia

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*Identyfikator GUID*<br/>
[in] Identyfikator GUID służący do ustawiania `guidPropertySet` pole [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) struktury.

### <a name="remarks"></a>Uwagi

To pole można ustawić za [Konstruktor](../../data/oledb/cdbpropidset-cdbpropidset.md) także. Wywołaj tę funkcję, jeśli używasz domyślnego konstruktora dla tej klasy.

## <a name="op_equal"></a> CDBPropIDSet::operator =

Przypisuje zawartość jednym Identyfikatorem właściwości zestawu do innego zbioru właściwości identyfikator.

### <a name="syntax"></a>Składnia

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)