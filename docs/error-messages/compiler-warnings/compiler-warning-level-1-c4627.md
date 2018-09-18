---
title: Kompilator ostrzeżenie (poziom 1) C4627 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fef8d0ab55205d2377fc52049c40a1c50151b93e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024180"
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

## <a name="see-also"></a>Zobacz też

[Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)
