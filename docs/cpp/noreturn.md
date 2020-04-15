---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: a30840aa0556a7324ba24c0f2aaec57dea88d082
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367855"
---
# <a name="noreturn"></a>noreturn

**Specyficzne dla firmy Microsoft**

Ten **atrybut __declspec** informuje kompilator, że funkcja nie zwraca. W związku z tym kompilator wie, że kod po wywołaniu funkcji **__declspec(noreturn)** jest nieosiągalny.

Jeśli kompilator znajdzie funkcję ze ścieżką sterującą, która nie zwraca wartości, generuje ostrzeżenie (C4715) lub komunikat o błędzie (C2202). Jeśli nie można osiągnąć ścieżki sterowania z powodu funkcji, która nigdy nie zwraca, można użyć **__declspec(noreturn),** aby zapobiec temu ostrzeżeniu lub błędowi.

> [!NOTE]
> Dodanie **__declspec(noreturn)** do funkcji, która ma zostać zwrócona, może spowodować niezdefiniowane zachowanie.

## <a name="example"></a>Przykład

W poniższej próbce **else** klauzula nie zawiera instrukcji return.  Deklarowanie `fatal` jako **__declspec(noreturn)** pozwala uniknąć błędu lub komunikatu ostrzegawczego.

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

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
