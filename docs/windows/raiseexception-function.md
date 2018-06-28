---
title: Raiseexception — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
dev_langs:
- C++
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2af97ac13386db450318f4d1f384517a8dd77baf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882186"
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
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)