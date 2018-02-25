---
title: IDBInitializeImpl::m_dwStatus | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
dev_langs:
- C++
helpviewer_keywords:
- m_dwStatus
ms.assetid: 7621ccff-ca60-4b75-9c6a-c104bd0e2038
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69c591b797908879f349945d49e6033763707592
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="idbinitializeimplmdwstatus"></a>IDBInitializeImpl::m_dwStatus
Flagi źródła danych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
DWORD m_dwStatus;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Te flagi określ lub wskazuje stan różnych atrybutów dla obiekt źródła danych. Zawiera co najmniej jeden z następujących `enum` wartości:  
  
```  
enum DATASOURCE_FLAGS {  
    DSF_MASK_INIT     = 0xFFFFF00F,  
    DSF_PERSIST_DIRTY = 0x00000001,  
    DSF_INITIALIZED   = 0x00000010,  
};  
```  
  
|||  
|-|-|  
|**DSF_MASK_INIT**|Maska umożliwiające przywróceniu niezainicjowanego stanu.|  
|**DSF_PERSIST_DIRTY**|Ustaw, jeśli obiekt źródła danych wymaga trwałości (jeśli wprowadzono zmiany).|  
|**DSF_INITIALIZED**|Zestaw, jeśli źródło danych został zainicjowany.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbinitializeimpl — klasa](../../data/oledb/idbinitializeimpl-class.md)   
 [IDBInitializeImpl::IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)   
 [IDBInitializeImpl::Uninitialize](../../data/oledb/idbinitializeimpl-uninitialize.md)