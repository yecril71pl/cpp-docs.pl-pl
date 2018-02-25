---
title: Klasa CAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1f0e893f300b7d89bee14ce28490328979d0fa17
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="caccessor-class"></a>Klasa CAccessor
Reprezentuje jeden z typów dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa rekordu użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 Jest używany, gdy rekord statycznie jest powiązana ze źródłem danych. Rekord zawiera buforu. Ta klasa obsługuje wiele metod dostępu w zestawie wierszy.  
  
 Użyj tego typu dostępu, gdy wiesz, struktury i typ bazy danych.  
  
 Jeśli Twoje akcesor zawiera pola, które wskazują pamięci (takich jak `BSTR` lub interface) który musi być zwolniony, wywołanie funkcji Członkowskich [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) podjęcia kolejnej rekord jest do odczytu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)