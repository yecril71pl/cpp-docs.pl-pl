---
title: noinline | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noinline_cpp
dev_langs:
- C++
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7a2831251d00f0dc24b1cfab7beeecaff100962
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092293"
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

