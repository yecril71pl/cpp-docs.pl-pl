---
title: InvokeModeOptions, struktura
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 315f1f0c49c4222bf525bbaf25c9ad0de8b9c7d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511702"
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

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)<br/>
[Klasa Microsoft::WRL::AgileEventSource](../windows/agileeventsource-class.md)