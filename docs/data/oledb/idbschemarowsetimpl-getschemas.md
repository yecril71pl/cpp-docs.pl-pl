---
title: IDBSchemaRowsetImpl::GetSchemas | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
dev_langs:
- C++
helpviewer_keywords:
- GetSchemas method
ms.assetid: fbe725a6-3acd-45f8-bcaf-10a6c1239cd2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 55ccad037b072e4d731462bbf89ff48b186bf068
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimplgetschemas"></a>IDBSchemaRowsetImpl::GetSchemas
Zwraca listę zestawów wierszy schematu dostępne dla [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (GetSchema s )(ULONG * pcSchemas,  
   GUID ** prgSchemas,  
   ULONG** prgRest);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pcSchemas*  
 [out] Wskaźnik do **ULONG** który jest wypełniony liczba schematów.  
  
 *prgSchemas*  
 [out] Wskaźnik do tablicy identyfikatorów GUID jest wypełniony za pomocą wskaźnika do tablicy identyfikatorów GUID zestaw wierszy schematu.  
  
 *prgRest*  
 [out] Wskaźnik do tablicy **ULONG**s, który ma zostać wypełnione tablica ograniczeń.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca tablicę wszystkich zestawów wierszy schematu obsługiwanego przez dostawcę. Zobacz [IDBSchemaRowset::GetSchemas](https://msdn.microsoft.com/en-us/library/ms719605.aspx) w systemie Windows SDK.  
  
 Implementacja tej funkcji wymaga od użytkownika posiadania schemat mapowania klasy sesji. Korzystając z informacji mapy schematu, następnie odpowiadały z tablicą identyfikatory GUID dla schematów w planie. Reprezentuje schematów obsługiwane przez dostawcę.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbschemarowsetimpl — klasa](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Elementy członkowskie idbschemarowsetimpl — klasa](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)   
 [IDBSchemaRowset::GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx)   
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)