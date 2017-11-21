---
title: IRowsetImpl::m_bCanScrollBack | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
dev_langs: C++
helpviewer_keywords: m_bCanScrollBack
ms.assetid: 69de3179-bf56-415e-935f-e98bcb34debe
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e64e0b63e3ddb06303f50bb774d736718ae59639
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplmbcanscrollback"></a>IRowsetImpl::m_bCanScrollBack
Wskazuje, czy dostawca może mieć wstecz jego przewijania kursora.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
unsigned  m_bCanScrollBack:1;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Połączone z **DBPROP_CANSCROLLBACKWARDS** właściwości w **DBPROPSET_ROWSET** grupy. Dostawca musi obsługiwać **DBPROP_CANSCROLLBACKWARDS** dla **m_bCanFetchBackwards** mieć wartość true.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetimpl — klasa](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)