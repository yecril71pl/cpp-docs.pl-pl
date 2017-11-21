---
title: Klasa CAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs: C++
helpviewer_keywords: CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 759ea7436124c1806ae26fb6a91a59d56c86d04a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="caccessor-class"></a>Klasa CAccessor
Reprezentuje jeden z typów dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      template < class   
      T  
       >  
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
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)