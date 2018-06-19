---
title: Struktura InvokeModeOptions | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5b1eb0e7f6cf49a7c6ac12a4810ae1622e263e2f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882840"
---
# <a name="invokemodeoptions-structure"></a>Struktura InvokeModeOptions

Określa, czy uruchomienie wszystkich zdarzeń w kolejce delegata lub zatrzymać wyzwalania po występuje błąd. Dopuszczalne wartości są określone w `InvokeMode` wyliczenia.

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

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)
[Microsoft::WRL::AgileEventSource — klasa](../windows/agileeventsource-class.md)