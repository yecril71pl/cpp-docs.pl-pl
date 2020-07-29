---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f0b5b17a6d64375f49a6d55021c72ba7119eb976
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213310"
---
# <a name="noreturn"></a>noreturn

**Specyficzne dla firmy Microsoft**

Ten **`__declspec`** atrybut informuje kompilator, że funkcja nie zwraca. W związku z tym kompilator wie, że kod następujący po wywołaniu **`__declspec(noreturn)`** funkcji jest nieosiągalny.

Jeśli kompilator odnajdzie funkcję z ścieżką kontrolną, która nie zwraca wartości, generuje ostrzeżenie (C4715) lub komunikat o błędzie (C2202). Jeśli nie można osiągnąć ścieżki sterującej ze względu na funkcję, która nigdy nie zwraca, można użyć, **`__declspec(noreturn)`** Aby zapobiec występowaniu tego ostrzeżenia lub błędu.

> [!NOTE]
> Dodanie **`__declspec(noreturn)`** do funkcji, która ma zostać zwrócona, może spowodować niezdefiniowane zachowanie.

## <a name="example"></a>Przykład

W poniższym przykładzie **`else`** klauzula nie zawiera instrukcji return.  Deklarowanie `fatal` jako eliminuje **`__declspec(noreturn)`** błąd lub komunikat ostrzegawczy.

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
