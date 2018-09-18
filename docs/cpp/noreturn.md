---
title: noreturn | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133fc70c5c2b8bb8f794746c1d5ca11be97b817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031044"
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