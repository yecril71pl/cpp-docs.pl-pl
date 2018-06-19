---
title: IDBSchemaRowsetImpl::GetRowset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
dev_langs:
- C++
helpviewer_keywords:
- GetRowset method
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ec479809bf95d4a88338401013b7f5980b703d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103752"
---
# <a name="idbschemarowsetimplgetrowset"></a>IDBSchemaRowsetImpl::GetRowset
Zwraca zestaw wierszy schematu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (GetRowset)(IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pUnkOuter`  
 [in] Zewnętrzne **IUnknown** podczas agregację; w przeciwnym razie **NULL**.  
  
 `rguidSchema`  
 [in] Odwołanie do zestawu wierszy schematu żądany identyfikator GUID (na przykład `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [in] Liczba ograniczeń, które ma zostać zastosowany do zestawu wierszy.  
  
 `rgRestrictions`  
 [in] Tablica `cRestrictions` **VARIANT**, które reprezentują ograniczenia.  
  
 `riid`  
 [in] Identyfikator IID do żądania zestawu wierszy schematu nowo utworzony.  
  
 `cPropertySets`  
 [in] Ustawia liczbę właściwości do ustawienia.  
  
 `rgPropertySets`  
 [We/Wy] Tablica [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury tak, aby ustawić dla zestawu wierszy schematu nowo utworzony.  
  
 `ppRowset`  
 [out] Wskaźnik do żądanego interfejsu na zestawu wierszy schematu nowo utworzony.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymaga od użytkownika posiadania schemat mapowania klasy sesji. Korzystając z informacji mapy schematu `GetRowset` tworzy obiekt danego zestawu wierszy, jeśli `rguidSchema` parametr jest równy jeden z wpisów map identyfikatorów GUID. Zobacz [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) opis wpisu mapy.  
  
 Zobacz [IDBSchemaRowset::GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx) w systemie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbschemarowsetimpl — klasa](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Elementy członkowskie idbschemarowsetimpl — klasa](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)