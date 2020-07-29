---
title: CDBPropSet — Klasa
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: 182db37a2a42ec91066b58903c873d3e9c8289f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216495"
---
# <a name="cdbpropset-class"></a>CDBPropSet — Klasa

Dziedziczy ze `DBPROPSET` struktury i dodaje konstruktora, który inicjuje pola klucza oraz `AddProperty` metodę dostępu.

## <a name="syntax"></a>Składnia

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AddProperty](#addproperty)|Dodaje właściwość do zestawu właściwości.|
|[CDBPropSet](#cdbpropset)|Konstruktor.|
|[SetGUID](#setguid)|Ustawia `guidPropertySet` pole `DBPROPSET` struktury.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_equal)|Przypisuje zawartość jednego zestawu właściwości do innej.|

## <a name="remarks"></a>Uwagi

Dostawcy OLE DB i konsumenci używają `DBPROPSET` struktur do przekazywania tablic `DBPROP` struktur. Każda `DBPROP` Struktura reprezentuje pojedynczą właściwość, którą można ustawić.

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a>CDBPropSet:: Add— Właściwość

Dodaje właściwość do zestawu właściwości.

### <a name="syntax"></a>Składnia

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>Parametry

*dwPropertyID*<br/>
podczas Identyfikator właściwości, która ma zostać dodana. Służy do inicjowania `dwPropertyID` `DBPROP` struktury dodanej do zestawu właściwości.

*funkcję*<br/>
podczas Wariant używany do zainicjowania wartości właściwości dla `DBPROP` struktury dodanej do zestawu właściwości.

*szValue*<br/>
podczas Ciąg używany do inicjowania wartości właściwości dla `DBPROP` struktury dodanej do zestawu właściwości.

*bValue*<br/>
podczas `BYTE`Wartość logiczna lub użyta do zainicjowania wartości właściwości dla `DBPROP` struktury dodanej do zestawu właściwości.

*nWartość*<br/>
podczas Wartość całkowita służąca do zainicjowania wartości właściwości dla `DBPROP` struktury dodanej do zestawu właściwości.

*fltValue*<br/>
podczas Wartość zmiennoprzecinkowa używana do inicjowania wartości właściwości dla `DBPROP` struktury dodanej do zestawu właściwości.

*dblValue*<br/>
podczas Wartość zmiennoprzecinkowa podwójnej precyzji używana do inicjowania wartości właściwości dla `DBPROP` struktury dodanej do zestawu właściwości.

*cyValue*<br/>
podczas Wartość waluty CY użyta do zainicjowania wartości właściwości dla `DBPROP` struktury dodanej do zestawu właściwości.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli właściwość została pomyślnie dodana. W przeciwnym razie **`false`** .

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a>CDBPropSet:: CDBPropSet

Konstruktor. Inicjuje `rgProperties` , `cProperties` i `guidPropertySet` pola struktury [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) .

### <a name="syntax"></a>Składnia

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID służący do inicjowania `guidPropertySet` pola.

*propset*<br/>
podczas Inny `CDBPropSet` obiekt dla konstruowania kopii.

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a>CDBPropSet:: SetGuid

Ustawia `guidPropertySet` pole w `DBPROPSET` strukturze.

### <a name="syntax"></a>Składnia

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID służący do ustawiania `guidPropertySet` pola struktury [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) .

### <a name="remarks"></a>Uwagi

To pole można również ustawić przez [konstruktora](../../data/oledb/cdbpropset-cdbpropset.md) .

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a>CDBPropSet:: operator =

Przypisuje zawartość jednego zestawu właściwości do innego zestawu właściwości.

### <a name="syntax"></a>Składnia

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Zobacz także

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Klasa CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET, struktura](/previous-versions/windows/desktop/ms714367(v=vs.85)) 
 [DBprop — struktura](/previous-versions/windows/desktop/ms717970(v=vs.85))
