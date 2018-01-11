---
title: "Semaphore::semaphore — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
dev_langs: C++
helpviewer_keywords: Semaphore, constructor
ms.assetid: 91c22ae7-181e-460d-ad40-70c3a53b26fd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c59d9843a727449bef48efac9980e9164225baae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="semaphoresemaphore-constructor"></a>Semaphore::Semaphore — Konstruktor
Inicjuje nowe wystąpienie klasy semafora.  
  
## <a name="syntax"></a>Składnia  
  
```  
explicit Semaphore(  
   HANDLE h  
);  
  
WRL_NOTHROW Semaphore(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Dojścia lub odwołania do r-wartości na obiekt semafora.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —
 
 ## <a name="see-also"></a>Zobacz też
 [Semaphore, klasa](../windows/semaphore-class.md)