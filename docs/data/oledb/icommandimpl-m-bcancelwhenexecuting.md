---
title: ICommandImpl::m_bCancelWhenExecuting | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
dev_langs: C++
helpviewer_keywords: m_bCancelWhenExecuting
ms.assetid: d7d33e4c-a862-4e6d-a9a1-4400bfe45b88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b668de0791734fda14a1a66684643f68630c8c60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="icommandimplmbcancelwhenexecuting"></a>ICommandImpl::m_bCancelWhenExecuting
Wskazuje, czy polecenie może być anulowane podczas wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
unsigned m_bCancelWhenExecuting:1;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie **true** (mogą zostać anulowane).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Icommandimpl — klasa](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)