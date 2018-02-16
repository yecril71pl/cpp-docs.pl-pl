---
title: IDBSchemaRowsetImpl::CreateSchemaRowset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateSchemaRowset method
ms.assetid: ad3e3e4d-45b9-461c-b7b8-3af6843631b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4975f452844a9efc8002b661efa224bf7cac8a3f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimplcreateschemarowset"></a>IDBSchemaRowsetImpl::CreateSchemaRowset
Implementuje funkcję twórcy obiektu COM dla obiekt określony przez parametr szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pUnkOuter`  
 [in] Zewnętrzne [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) podczas agregowania, w przeciwnym razie **NULL**.  
  
 `cRestrictions`  
 [in] Liczba ograniczeń stosowany do wierszy schematu.  
  
 `rgRestrictions`  
 [in] Tablica `cRestrictions` **VARIANT**s ma zostać zastosowany do zestawu wierszy.  
  
 `riid`  
 [in] Interfejs do [QueryInterface](../../atl/queryinterface.md) dla na dane wyjściowe **IUnknown**.  
  
 `cPropertySets`  
 [in] Ustawia liczbę właściwości do ustawienia.  
  
 `rgPropertySets`  
 [in] Tablica [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury określające właściwości są ustawione.  
  
 `ppRowset`  
 [out] Wychodzącej **IUnknown** zażądał `riid`. To **IUnknown** jest interfejsem obiektu zestawu wierszy schematu.  
  
 `pSchemaRowset`  
 [out] Wskaźnik do wystąpienia klasy zestawu wierszy schematu. Zazwyczaj ten parametr nie jest używany, ale można używać, jeśli konieczne jest przeprowadzenie więcej pracy na zestaw wierszy schematu przed przekazaniem ich do obiektu COM. Okres istnienia `pSchemaRowset` jest powiązany `ppRowset`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja implementuje ogólnego twórcy dla wszystkich typów zestawów wierszy schematu. Zazwyczaj użytkownik nie wywołują tę funkcję. Jest ona wywoływana przez wykonanie mapowania schematu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbschemarowsetimpl — klasa](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Elementy członkowskie idbschemarowsetimpl — klasa](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)