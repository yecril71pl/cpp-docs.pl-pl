---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f9ca61c9d734ccdd6b8d8374ed3a7c4128ee3d5e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857375"
---
# <a name="noreturn"></a>noreturn

**Microsoft Specific**

Ten atrybut **__declspec** informuje kompilator, że funkcja nie zwraca. W związku z tym kompilator wie, że kod następujący po wywołaniu funkcji **__declspec (noreturn)** jest nieosiągalny.

Jeśli kompilator odnajdzie funkcję z ścieżką kontrolną, która nie zwraca wartości, generuje ostrzeżenie (C4715) lub komunikat o błędzie (C2202). Jeśli nie można osiągnąć ścieżki sterującej ze względu na funkcję, która nigdy nie zwraca, można użyć **__declspec (noreturn)** , aby uniknąć tego ostrzeżenia lub błędu.

> [!NOTE]
>  Dodanie **__declspec (noreturn)** do funkcji, która powinna zostać zwrócona, może spowodować niezdefiniowane zachowanie.

## <a name="example"></a>Przykład

W poniższym przykładzie klauzula **else** nie zawiera instrukcji return.  Deklarowanie `fatal` jako **__declspec (noreturn)** zapobiega błędowi lub komunikatowi ostrzegawczemu.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)