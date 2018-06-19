---
title: EventSource::InvokeAll — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 00bce09f9e081bb0cd5c01115b05e4d3268d7293
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882618"
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll — Metoda
Wywołuje każdy program obsługi zdarzeń skojarzonych z bieżącym [EventSource](../windows/eventsource-class.md) przy użyciu określone typy argumentów i argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `T0`  
 Typ argumentu procedury obsługi zdarzeń zeroth.  
  
 `T1`  
 Typ pierwszego argumentu procedury obsługi zdarzeń.  
  
 `T2`  
 Typ drugiego argumentu procedury obsługi zdarzeń.  
  
 `T3`  
 Typ trzeciego argumentu procedury obsługi zdarzeń.  
  
 `T4`  
 Typ czwartego argumentu procedury obsługi zdarzeń.  
  
 `T5`  
 Typ piątego argument procedury obsługi zdarzeń.  
  
 `T6`  
 Typ szóstego argument procedury obsługi zdarzeń.  
  
 `T7`  
 Typ siódmego argument procedury obsługi zdarzeń.  
  
 `T8`  
 Typ argumentu osiem obsługi zdarzenia.  
  
 `T9`  
 Typ dziewiąty argument procedury obsługi zdarzeń.  
  
 `arg0`  
 Zeroth argument procedury obsługi zdarzeń.  
  
 `arg1`  
 Pierwszy argument procedury obsługi zdarzeń.  
  
 `arg2`  
 Drugi argument procedury obsługi zdarzeń.  
  
 `arg3`  
 Trzeci argument procedury obsługi zdarzeń.  
  
 `arg4`  
 Czwarty argument procedury obsługi zdarzeń.  
  
 `arg5`  
 Piąty argument procedury obsługi zdarzeń.  
  
 `arg6`  
 Argument szóstego programu obsługi zdarzeń.  
  
 `arg7`  
 Argument siódmego programu obsługi zdarzeń.  
  
 `arg8`  
 Osiem argument procedury obsługi zdarzeń.  
  
 `arg9`  
 Dziewiąty argument procedury obsługi zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)