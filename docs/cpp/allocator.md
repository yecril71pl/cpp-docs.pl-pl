---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: f9c8de7c8686b89a2ab9570a2558e3f649e545b5
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58417084"
---
# <a name="allocator"></a>allocator

**Microsoft Specific**

**Alokatora** Specyfikator deklaracji może odnosić się do funkcji niestandardowych alokacji pamięci, aby uwidocznić alokacje za pośrednictwem śledzenie zdarzeń dla Windows (ETW).

## <a name="syntax"></a>Składnia

```
   __declspec(allocator) 
```

## <a name="remarks"></a>Uwagi

Profiler pamięci natywnej w programie Visual Studio polega na zbieranie alokacji dane zdarzeń ETW wyemitowane przez w czasie wykonywania. Puli buforów w CRT i zestaw Windows SDK ma została oznaczona na poziomie źródła przechwycić swoje dane alokacji. Jeśli piszesz własnego puli buforów, a następnie wszystkie funkcje, które zwracają wskaźnik do nowo przydzielonego stosu pamięci może być dekorowane za pomocą `__declspec(allocator)`, jak pokazano w następującym przykładzie myMalloc:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Aby uzyskać więcej informacji, zobacz [pomiaru wykorzystania pamięci w programie Visual Studio](/visualstudio/profiling/memory-usage) i [niestandardowe zdarzenia ETW sterty natywnej](/visualstudio/profiling/custom-native-etw-heap-events).