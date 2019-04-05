---
title: InvokeModeOptions, struktura
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 0e5b45042c9959b87ad5db97ab755e49de469149
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035283"
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions, struktura

Określa, czy do uruchamiania wszystkich zdarzeń w kolejce delegata lub aby zatrzymać wyzwalania po występuje błąd. Dopuszczalne wartości są określone w `InvokeMode` wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL — Przestrzeń nazw](microsoft-wrl-namespace.md)<br/>
[Klasa Microsoft::WRL::AgileEventSource](agileeventsource-class.md)