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
ms.openlocfilehash: 12032318f898b2986b64d5cd8a1e611a31d1fc8c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372395"
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

*godz.*<br/>
Kod wyjątku wyjątków zgłaszanych; oznacza to, że wartość HRESULT operację zakończoną niepowodzeniem.

*dwExceptionFlags*<br/>
Flaga wskazująca pozwala na kontynuację wyjątek (wartość flagi wynosi zero), lub noncontinuable wyjątek (wartość flagi jest różna od zera). Domyślnie wyjątek jest wystąpieniu.

## <a name="remarks"></a>Uwagi

Zgłasza wyjątek w wątku wywołującego.

Aby uzyskać więcej informacji, zobacz Windows `RaiseException` funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)