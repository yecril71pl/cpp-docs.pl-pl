---
title: RaiseException — funkcja | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5426d639ffb8655466239232da7672b89564bfae
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020112"
---
# <a name="raiseexception-function"></a>RaiseException — Funkcja
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
### <a name="parameters"></a>Parametry  
 *godz.*  
 Kod wyjątku wyjątków zgłaszanych; oznacza to, że wartość HRESULT operację zakończoną niepowodzeniem.  
  
 *dwExceptionFlags*  
 Flaga wskazująca pozwala na kontynuację wyjątek (wartość flagi wynosi zero), lub noncontinuable wyjątek (wartość flagi jest różna od zera). Domyślnie wyjątek jest wystąpieniu.  
  
## <a name="remarks"></a>Uwagi  
 Zgłasza wyjątek w wątku wywołującego.  
  
 Aby uzyskać więcej informacji, zobacz Windows `RaiseException` funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)