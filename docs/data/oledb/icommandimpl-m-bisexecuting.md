---
title: ICommandImpl::m_bIsExecuting | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
dev_langs: C++
helpviewer_keywords: m_bIsExecuting
ms.assetid: 1e152164-514c-4116-88a3-16984af99991
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f65bba12d56ec8e73dacd661ba551aa6e3ea636b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="icommandimplmbisexecuting"></a>ICommandImpl::m_bIsExecuting
Wskazuje, czy polecenie jest aktualnie wykonywany.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
unsigned m_bIsExecuting:1;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Execute** metody klasy polecenia można ustawić tę zmienną **true**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Icommandimpl — klasa](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)