---
title: "Semaphore::operator = — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7608c05c5915a3b4d04cf6a12e1b424e6b44ab4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= Operator
Przenosi bieżący obiekt semafora określone dojście z obiektu semafora.  
  
## <a name="syntax"></a>Składnia  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 R-wartości — odwołanie do obiektu semafora.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego obiektu semafora.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —
 
 ## <a name="see-also"></a>Zobacz też
 [Semaphore, klasa](../windows/semaphore-class.md)