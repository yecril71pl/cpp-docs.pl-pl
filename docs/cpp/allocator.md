---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 39708e8cfff7f61c3a3f763f87e1a3da36f0d4b1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077254"
---
# <a name="allocator"></a>allocator

**Specyficzne dla firmy Microsoft**

Specyfikator deklaracji **alokatora** można zastosować do funkcji niestandardowych alokacji pamięci, aby udostępnić alokacje za pośrednictwem śledzenia zdarzeń dla systemu Windows (ETW).

## <a name="syntax"></a>Składnia

```
   __declspec(allocator)
```

## <a name="remarks"></a>Uwagi

Profiler pamięci natywnej w programie Visual Studio działa przez zbieranie danych zdarzeń ETW alokacji emitowanych przez środowisko uruchomieniowe. Puli buforów w CRT i zestaw Windows SDK ma została oznaczona na poziomie źródła przechwycić swoje dane alokacji. W przypadku pisania własnych przydziałów, wszystkie funkcje, które zwracają wskaźnik do nowo przydzieloną pamięci sterty, mogą być dekoracyjne `__declspec(allocator)`, jak pokazano w tym przykładzie dla elementu malloc:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Aby uzyskać więcej informacji, zobacz [miary użycie pamięci w Visual Studio](/visualstudio/profiling/memory-usage) i [niestandardowe zdarzenia sterty ETW](/visualstudio/profiling/custom-native-etw-heap-events).

**ZAKOŃCZENIE określonych przez firmę Microsoft**
