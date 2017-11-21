---
title: "Raiseexception — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::RaiseException
dev_langs: C++
helpviewer_keywords: RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f64d0e38bb92f9ebe3954b47ece29184cbf1a73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="raiseexception-function"></a>RaiseException — Funkcja
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 Kod wyjątku wyjątków zgłaszanych; oznacza to, HRESULT operację zakończoną niepowodzeniem.  
  
 `dwExceptionFlags`  
 Flaga, która wskazuje, można kontynuować wyjątek (wartość flagi wynosi zero), czy wyjątek noncontinuable (wartość flagi jest różna od zera). Domyślnie wyjątek jest wystąpieniu.  
  
## <a name="remarks"></a>Uwagi  
 Zgłasza wyjątek w wątku wywołującym.  
  
 Aby uzyskać więcej informacji, zobacz Windows **raiseexception —** funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)