---
title: Cdbpropset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6d62b8d4b033d1b90c753d5de1752f0cb737f0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114660"
---
# <a name="cdbpropset-class"></a>CDBPropSet — Klasa

Dziedziczy `DBPROPSET` struktury i dodaje konstruktora, który inicjuje pola klucza, jak również `AddProperty` dostęp do metody.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDBPropSet : public tagDBPROPSET  
```  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldbcli.h  

## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[addProperty](#addproperty)|Dodaje właściwość do zestawu właściwości.|  
|[CDBPropSet](#cdbpropset)|Konstruktor.|  
|[Setguid —](#setguid)|Zestawy `guidPropertySet` pole `DBPROPSET` struktury.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#op_equal)|Przypisuje zawartość jednej właściwości do innego zestawu.|  
  
## <a name="remarks"></a>Uwagi  

Użycie dostawcy i konsumentów OLE DB `DBPROPSET` struktury do przekazywania tablic `DBPROP` struktury. Każdy `DBPROP` struktury reprezentuje jedną właściwość, która może być ustawiona.  

## <a name="addproperty"></a> CDBPropSet::AddProperty

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
[in] Identyfikator właściwości do dodania. Używane do zainicjowania `dwPropertyID` z `DBPROP` struktury dodane do zestawu właściwości.  
  
*var*<br/>
[in] Wariant używane do zainicjowania wartości właściwości dla `DBPROP` struktury dodane do zestawu właściwości.  
  
*szValue*<br/>
[in] Ciąg używany do inicjowania wartości właściwości dla `DBPROP` struktury dodane do zestawu właściwości.  
  
*bDane wartości*<br/>
[in] A `BYTE` lub wartość logiczną, używane do zainicjowania wartości właściwości dla `DBPROP` struktury dodane do zestawu właściwości.  
  
*nWartość:*<br/>
[in] Wartość całkowitą, używane do zainicjowania wartości właściwości dla `DBPROP` struktury dodane do zestawu właściwości.  
  
*fltValue*<br/>
[in] Wartość zmiennoprzecinkowa, używane do zainicjowania wartości właściwości dla `DBPROP` struktury dodane do zestawu właściwości.  
  
*dblValue*<br/>
[in] Wartość zmiennoprzecinkowa podwójnej precyzji, używane do zainicjowania wartości właściwości dla `DBPROP` struktury dodane do zestawu właściwości.  
  
*cyValue*<br/>
[in] Używane do zainicjowania wartości właściwości dla wartości waluty CY `DBPROP` struktury dodane do zestawu właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  

**wartość true,** Jeśli właściwość została pomyślnie dodana. W przeciwnym razie **false**. 

## <a name="cdbpropset"></a> CDBPropSet::CDBPropSet

Konstruktor. Inicjuje `rgProperties`, `cProperties`, i `guidPropertySet` pola [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CDBPropSet(const GUID& guid);  

CDBPropSet(const CDBPropSet& propset);  

CDBPropSet();  
```  
  
#### <a name="parameters"></a>Parametry  

*Identyfikator GUID*<br/>
[in] Identyfikator GUID służący do zainicjowania `guidPropertySet` pola.  
  
*zestaw właściwości*<br/>
[in] Inny `CDBPropSet` obiekt do tworzenia kopii.  

## <a name="setguid"></a> CDBPropSet::SetGUID

Zestawy `guidPropertySet` pole `DBPROPSET` struktury.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*Identyfikator GUID*<br/>
[in] Identyfikator GUID służący do ustawiania `guidPropertySet` pole [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury.  
  
### <a name="remarks"></a>Uwagi  

To pole można ustawić za [Konstruktor](../../data/oledb/cdbpropset-cdbpropset.md) także.  

## <a name="op_equal"></a> CDBPropSet::operator =

Przypisuje zawartość jedną właściwość, ustaw do innego zbioru właściwości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();  
```  
  
## <a name="see-also"></a>Zobacz też  

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet, klasa](../../data/oledb/cdbpropidset-class.md)<br/>
[Struktura DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))   
[Struktura DBPROP](/previous-versions/windows/desktop/ms717970\(v=vs.85\))