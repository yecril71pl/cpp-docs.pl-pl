---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: 1d78e8f5116eabf9073205b938156197bf1001a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245248"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

To **__declspec** atrybut informuje kompilator, że funkcja nie zwraca. W rezultacie, kompilator wie, że kod następujący po wywołaniu **__declspec(noreturn)** funkcji jest nieosiągalny.

Jeśli kompilator znajdzie funkcji ze ścieżką kontroli, która nie zwraca wartości, generuje ostrzeżenie (C4715) lub komunikat o błędzie (C2202). Jeśli ścieżka kontroli jest nieosiągalny z powodu funkcja, która nigdy nie powraca, możesz użyć **__declspec(noreturn)** Aby uniknąć tego ostrzeżenia lub błędu.

> [!NOTE]
>  Dodawanie **__declspec(noreturn)** do funkcji, która powinna zwrócić może spowodować niezdefiniowane zachowanie.

## <a name="example"></a>Przykład

W poniższym przykładzie **else** klauzuli nie zawiera instrukcji return.  Deklarowanie `fatal` jako **__declspec(noreturn)** pozwala uniknąć błąd lub ostrzeżenie.

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

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)