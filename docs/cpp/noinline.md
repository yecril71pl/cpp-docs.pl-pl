---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: e155726ad1f2f3f6f0501d3aebf7fa14e620d6bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377405"
---
# <a name="noinline"></a>noinline

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

**__declspec(noinline)** informuje kompilator, aby nigdy nie wbudowanej funkcji określonej składowej (funkcja w klasie).

Możliwe zorientowane na wbudowanej funkcji jest mały i nie mają kluczowe znaczenie dla wydajności kodu. Oznacza to jeśli funkcja jest mały i nie mogą być wywoływana często, takich jak funkcja obsługująca warunek błędu.

Należy pamiętać, że jeśli funkcja jest oznaczona **noinline**, funkcja wywołująca będzie mniejsze i w związku z tym, sama kandydatem do kompilatora wbudowanie.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[w tekście, __inline, \__forceinline](inline-functions-cpp.md)
