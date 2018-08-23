---
title: EventSource::InvokeAll, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::InvokeAll
dev_langs:
- C++
helpviewer_keywords:
- InvokeAll method
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57450abdef0a6b25731405e092520ec5589972a1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613738"
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll — Metoda

Wywołuje każdy program obsługi zdarzeń skojarzonych z bieżącym [EventSource](../windows/eventsource-class.md) przy użyciu określone typy argumentów i argumenty.

## <a name="syntax"></a>Składnia

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Parametry

*T0*  
Typ argumentu procedury obsługi zdarzeń zerowego.

*T1*  
Typ pierwszego argumentu procedury obsługi zdarzeń.

*T2*  
Typ drugiego argumentu procedury obsługi zdarzeń.

*T3*  
Typ trzeciego argumentu procedury obsługi zdarzeń.

*T4*  
Typ czwartego argumentu procedury obsługi zdarzeń.

*T5*  
Typ piątego argumentu procedury obsługi zdarzeń.

*T6*  
Typ szóstego argumentu procedury obsługi zdarzeń.

*T7*  
Typ siódmego argumentu procedury obsługi zdarzeń.

*T8*  
Typ ósmego argumentu procedury obsługi zdarzeń.

*T9*  
Typ dziewiątego argumentu procedury obsługi zdarzeń.

*arg0*  
Argument procedury obsługi zdarzeń zerowego.

*arg1*  
Pierwszy argument procedury obsługi zdarzeń.

*argument2*  
Drugi argument procedury obsługi zdarzeń.

*arg3*  
Trzeci argument procedury obsługi zdarzeń.

*Arg4*  
Czwarty argument procedury obsługi zdarzeń.

*arg5*  
Piąty argument procedury obsługi zdarzeń.

*arg6*  
Szósty argument procedury obsługi zdarzeń.

*arg7*  
Siódmego argumentu procedury obsługi zdarzeń.

*arg8*  
Identyfikator ósmego argumentu procedury obsługi zdarzenia.

*arg9*  
Dziewiątego argumentu procedury obsługi zdarzeń.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
[EventSource, klasa](../windows/eventsource-class.md)