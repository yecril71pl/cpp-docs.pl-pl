---
title: IRowsetImpl::m_bCanFetchBack | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
dev_langs: C++
helpviewer_keywords: m_bCanFetchBack
ms.assetid: cfa007b0-7ba5-48a3-9d05-9f1916305fb7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 09440f8453fe0ee13297c600b148927bacafc5da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplmbcanfetchback"></a>IRowsetImpl::m_bCanFetchBack
Wskazuje, czy dostawca obsługuje pobieranie z poprzednimi wersjami.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
unsigned m_bCanFetchBack:1;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Połączone z **DBPROP_CANFETCHBACKWARDS** właściwości w **DBPROPSET_ROWSET** grupy. Dostawca musi obsługiwać **DBPROP_CANFETCHBACKWARDS** dla **m_bCanFetchBackwards** mieć wartość true.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetimpl — klasa](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)