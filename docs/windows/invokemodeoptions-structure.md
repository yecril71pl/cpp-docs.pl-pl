---
title: Struktura InvokeModeOptions | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
- event/Microsoft::WRL::InvokeMode
dev_langs:
- C++
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b27789f582b383530a675da83456a100780760b4
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="invokemodeoptions-structure"></a>Struktura InvokeModeOptions

Określa, czy uruchomienie wszystkich zdarzeń w kolejce delegata lub zatrzymać wyzwalania po występuje błąd. Dopuszczalne wartości są określone w `InvokeMode` wyliczenia.

## <a name="syntax"></a>Składnia

```
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

 **Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)
[Microsoft::WRL::AgileEventSource — klasa](../windows/agileeventsource-class.md)