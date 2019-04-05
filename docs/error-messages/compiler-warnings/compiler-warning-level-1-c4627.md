---
title: Kompilator ostrzeżenie (poziom 1) C4627
ms.date: 09/09/2018
f1_keywords:
- C4627
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
ms.openlocfilehash: 06db3d7e585dfe49b2e0854973f63834648613b7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039666"
---
# <a name="compiler-warning-level-1-c4627"></a>Kompilator ostrzeżenie (poziom 1) C4627

> "*header_file*": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka

Jeśli bieżącego pliku źródłowego ma [/Yu \(Użyj prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) zestaw, opcji, a następnie Kompilator ignoruje całą zawartość pliku, zanim prekompilowany plik nagłówkowy jest dołączony. Ostrzeżenie **C4627** jest generowany w programie Visual Studio 2015 i starsze wersje, jeśli *header_file* znajduje się przed prekompilowanego pliku nagłówkowego, i jeśli prekompilowanego pliku nagłówkowego nie obejmuje również *header_file*.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak może wystąpić błąd i pokazuje, jak go naprawić:

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>Zobacz także

[Tworzenie prekompilowanych plików nagłówka](../../build/creating-precompiled-header-files.md)
