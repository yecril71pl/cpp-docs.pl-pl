---
title: IDBSchemaRowsetImpl::GetRowset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
dev_langs: C++
helpviewer_keywords: GetRowset method
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5164bcd56c61868649af6185c8b84ebf20098b18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idbschemarowsetimplgetrowset"></a>IDBSchemaRowsetImpl::GetRowset
Zwraca zestaw wierszy schematu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD (GetRowset)(  
   IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset   
);  
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