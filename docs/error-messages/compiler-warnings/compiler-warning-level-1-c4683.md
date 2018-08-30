---
title: Kompilator ostrzeżenie (poziom 1) C4683 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a157d3beb7c2efa7f1144a961973652e2ce384f7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194200"
---
# <a name="compiler-warning-level-1-c4683"></a>Kompilator ostrzeżenie (poziom 1) C4683

> "*funkcja*": źródło zdarzenia ma "out" — parametru; wskazana jest ostrożność podczas podłączania wielu obsług zdarzeń

## <a name="remarks"></a>Uwagi

Jeśli więcej niż jeden obiekt sink zdarzenia nasłuchuje ze źródłem zdarzeń COM, wartość parametru wyjściowego można zignorować.

Należy pamiętać, że nastąpi przeciek pamięci, w następujących sytuacjach:

1. Jeśli metoda ma przydzielanej wewnętrznie, na przykład ciąg BSTR parametru wyjściowego *.

2. Jeśli zdarzenie ma więcej niż jeden program obsługi (jest to zdarzenie multiemisji).

Przyczyną przecieku jest, że parametr out zostaną ustawione przez więcej niż jeden program obsługi, ale zwracany do witryny wywołania przez ostatnią procedurę obsługi.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4683 i pokazuje, jak go naprawić:

```cpp
// C4683.cpp
// compile with: /W1 /LD
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="xx") ];

[ object ]
__interface I {
   HRESULT f([out] int* pi);
   // try the following line instead
   // HRESULT f(int* pi);
};

[ coclass, event_source(com) ]
struct E {
   __event __interface I;   // C4683
};
```