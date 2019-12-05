---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: 6e424846c46dd50852b62008c4f1f38827da849c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857414"
---
# <a name="noinline"></a>noinline

**Microsoft Specific**

**__declspec (NoLine)** instruuje kompilator, aby nigdy nie wbudowana do określonej funkcji elementu członkowskiego (funkcja w klasie).

Może być wartościowa niewbudowaną funkcję, jeśli jest ona mała i nie ma znaczenia dla wydajności kodu. Oznacza to, że jeśli funkcja jest mała i prawdopodobnie nie jest często wywoływana, na przykład funkcja, która obsługuje warunek błędu.

Należy pamiętać, że jeśli funkcja jest oznaczona jako **NoLine**, funkcja wywołująca będzie mniejsza i w ten sposób sama jest kandydatem do dekreślenia kompilatora.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[wbudowane, __inline, \__forceinline](inline-functions-cpp.md)
