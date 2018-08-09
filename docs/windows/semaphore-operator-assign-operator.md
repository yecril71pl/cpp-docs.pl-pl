---
title: Semaphore::operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eee563a52a24d2b78157b640ae6e84217c03af64
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651281"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= Operator
Przenosi określone dojście z **semafora** obiekt do bieżącego **semafora** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odwołania Rvalue do **semafora** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego **semafora** obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers
 
 ## <a name="see-also"></a>Zobacz też
 [Semaphore, klasa](../windows/semaphore-class.md)