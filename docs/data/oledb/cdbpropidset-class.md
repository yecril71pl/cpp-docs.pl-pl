---
title: Cdbpropidset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6ab6e58ad6f25232be5c298673cefe6d0488f63b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083103"
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
|[Addpropertyid —](#addpropertyid)|Dodaje właściwość do zestawu identyfikator właściwości.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor.|
|[Setguid —](#setguid)|Ustawia ustawiony identyfikator GUID Identyfikatora właściwości.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_equal)|Przypisuje zawartość jednym Identyfikatorem właściwości zestawu do drugiego.|

## <a name="remarks"></a>Uwagi

Użyj konsumentów OLE DB `DBPROPIDSET` struktur, aby przekazać tablicę identyfikatorów właściwości, dla których użytkownik chce uzyskać informacje o właściwościach. Właściwości określone w pojedynczej [DBPROPIDSET](/previous-versions/windows/desktop/ms717981) struktury należą do zestawu jednej właściwości.

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

Konstruktor. Inicjuje `rgProperties`, `cProperties`oraz (opcjonalnie) `guidPropertySet` pola [DBPROPIDSET](/previous-versions/windows/desktop/ms717981) struktury.

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
[in] Identyfikator GUID służący do ustawiania `guidPropertySet` pole [DBPROPIDSET](/previous-versions/windows/desktop/ms717981) struktury.

### <a name="remarks"></a>Uwagi

To pole można ustawić za [Konstruktor](../../data/oledb/cdbpropidset-cdbpropidset.md) także. Wywołaj tę funkcję, jeśli używasz domyślnego konstruktora dla tej klasy.

## <a name="op_equal"></a> CDBPropIDSet::operator =

Przypisuje zawartość jednym Identyfikatorem właściwości zestawu do innego zbioru właściwości identyfikator.

### <a name="syntax"></a>Składnia

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)