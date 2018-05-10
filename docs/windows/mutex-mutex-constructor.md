---
title: Mutex::mutex — Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb7782e44fc8598ca3b806ef922f8d0840765e28
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex — Konstruktor
Inicjuje nowe wystąpienie klasy obiektu Mutex.  
  
## <a name="syntax"></a>Składnia  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Dojścia lub odwołania do r-wartości uchwytu do obiektu Mutex.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje obiekt Mutex z określonego dojścia. Drugi Konstruktor inicjuje obiekt Mutex z określonego dojścia, a następnie przenosi prawo własności obiektu mutex do bieżącego obiektu Mutex.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —
 
 ## <a name="see-also"></a>Zobacz też
 [Mutex — klasa](../windows/mutex-class1.md)