---
title: Konwersje standardowe i niejawne konwersje boxing
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, implicit
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
ms.openlocfilehash: 086de06159b8d9195b4a4a275af8a95f56a46ce3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438020"
---
# <a name="standard-conversions-and-implicit-boxing"></a>Konwersje standardowe i niejawne konwersje boxing

Konwersja standardowa zostanie wybrany przez kompilator za pośrednictwem konwersji, która wymaga opakowania.

## <a name="example"></a>Przykład

```
// clr_implicit_boxing_Std_conversion.cpp
// compile with: /clr
int f3(int ^ i) {   // requires boxing
   return 1;
}

int f3(char c) {   // no boxing required, standard conversion
   return 2;
}

int main() {
   int i = 5;
   System::Console::WriteLine(f3(i));
}
```

```Output
2
```

## <a name="see-also"></a>Zobacz też

[Konwersja boxing](../windows/boxing-cpp-component-extensions.md)