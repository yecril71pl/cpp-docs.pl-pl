---
title: InvokeModeOptions, struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea549db29f7fcb67e4d59e341bf7d5ad085b6d7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392713"
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