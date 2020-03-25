---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f37ce13e27f9b141eab928b88102813a5b6d65f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177888"
---
# <a name="noreturn"></a>noreturn

**Specyficzne dla firmy Microsoft**

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

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
