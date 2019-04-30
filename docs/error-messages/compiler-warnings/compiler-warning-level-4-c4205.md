---
title: Kompilator ostrzeżenie (poziom 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 1b165d2bdb2fb50df89fdd77c734c054a40b6e95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401231"
---
# <a name="compiler-warning-level-4-c4205"></a>Kompilator ostrzeżenie (poziom 4) C4205

użyto niestandardowego rozszerzenia: deklaracja statycznej funkcji występuje w zakresie funkcji

Z rozszerzeniami firmy Microsoft (/Ze) **statyczne** funkcje mogą być zadeklarowane wewnątrz innej funkcji. Funkcja znajduje się zakresie globalnym.

## <a name="example"></a>Przykład

```
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

Takie inicjalizacje są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).