---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: bedf17072c06ec893b9cbd83b46403dcd3bc1560
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186688"
---
# <a name="noinline"></a>noinline

**Specyficzne dla firmy Microsoft**

**`__declspec(noinline)`** instruuje kompilator, aby nigdy nie wbudowanł określonej funkcji elementu członkowskiego (funkcja w klasie).

Może być wartościowa niewbudowaną funkcję, jeśli jest ona mała i nie ma znaczenia dla wydajności kodu. Oznacza to, że jeśli funkcja jest mała i prawdopodobnie nie jest często wywoływana, na przykład funkcja, która obsługuje warunek błędu.

Należy pamiętać, że jeśli funkcja jest oznaczona **`noinline`** , funkcja wywołująca będzie mniejsza i w ten sposób sama jest kandydatem do dekreślenia kompilatora.

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
[inline, __inline, \_ _forceinline](inline-functions-cpp.md)
