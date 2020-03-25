---
title: Problemy ze śródwierszowaniem funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: cb4653bd2f03683b9abad1eea0e9ffa88222090e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184245"
---
# <a name="function-inlining-problems"></a>Problemy ze śródwierszowaniem funkcji

W przypadku korzystania z funkcji dekreślenia należy:

- Mają wbudowane funkcje zaimplementowane w pliku nagłówkowym, który zawiera.

- Włączenie funkcji tworzenia konspektu w pliku nagłówkowym.

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

a następnie

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

Jeśli używasz dyrektywy kompilatora `#pragma inline_depth`, upewnij się, że jest ustawiona wartość 2 lub większa. Wartość zerowa spowoduje wyłączenie funkcji tworzenia konspektu. Upewnij się również, że używasz opcji kompilatora **/OB1** lub **/Ob2** .

Mieszanie wbudowanych i niewbudowanych opcji kompilacji w różnych modułach może czasami spowodować problemy. Jeśli C++ biblioteka jest tworzona z włączonym wykreśleniem funkcji ([/OB1](../../build/reference/ob-inline-function-expansion.md) lub [/Ob2](../../build/reference/ob-inline-function-expansion.md)), ale odpowiedni plik nagłówkowy opisujący funkcje ma wyłączone wyłączenie (Brak opcji), zostanie wyświetlony komunikat o błędzie LNK2001. Funkcje nie są uwzględniane w kodzie z pliku nagłówkowego, ale ponieważ nie znajdują się w pliku biblioteki, nie ma adresu do rozpoznania odwołania.

Podobnie, projekt, który używa funkcji, definiuje jeszcze funkcje w pliku. cpp, a nie w pliku nagłówkowym, również otrzymuje LNK2019. Plik nagłówkowy jest uwzględniany wszędzie tam, gdzie jest to odpowiednie, ale funkcje są podkreślane tylko wtedy, gdy plik. cpp przechodzi przez kompilator; w związku z tym konsolidator widzi funkcje jako nierozwiązane zewnętrzne, gdy są używane w innych modułach.

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

a następnie

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

a następnie

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>Zobacz też

[Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
