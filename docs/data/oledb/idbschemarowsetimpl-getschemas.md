---
title: IDBSchemaRowsetImpl::GetSchemas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 886b3ea82d8eb0193207438ce7c5a4fc51981cbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103310"
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