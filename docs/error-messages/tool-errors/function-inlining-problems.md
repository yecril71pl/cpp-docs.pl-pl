---
title: Problemy ze Śródwierszowaniem funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98d0ed20881ef89264f7c162750f600c7f68412b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088140"
---
# <a name="function-inlining-problems"></a>Problemy ze śródwierszowaniem funkcji

Jeśli korzystasz ze śródwierszowaniem funkcji, musisz mieć:

- Ma wbudowane funkcje implementowane w pliku nagłówkowym, które należy uwzględnić.

- Masz wbudowanie włączone w pliku nagłówkowym.

```
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

Następnie wyszukaj maszynę

```
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

Jeśli używasz `#pragma inline_depth` kompilatora dyrektywy, upewnij się, że ma wartość 2 lub nowszej. Wartość zero spowoduje wyłączenie wbudowanie. Upewnij się, używane są również **/Ob1** lub **/ob2** opcje kompilatora.

Mieszanie wbudowane i innych niż inline opcji kompilacji na różnych modułów może czasami powodować problemy. Jeśli biblioteka języka C++ jest tworzony za pomocą funkcji wbudowanie włączona ([/Ob1](../../build/reference/ob-inline-function-expansion.md) lub [/ob2](../../build/reference/ob-inline-function-expansion.md)), ale odpowiedni plik nagłówkowy zawierająca opis funkcji ma wbudowanie wyłączone (nie opcji), otrzymasz błąd LNK2001. Funkcji nie może korzystać z pliku nagłówka w wbudowana w kodzie, ale ponieważ nie znajdują się w pliku biblioteki nie ma żadnego adresu rozpoznać odwołania.

Podobnie projekt, który korzysta ze śródwierszowaniem funkcji jeszcze Określa funkcje w pliku .cpp, a nie w nagłówku pliku otrzymają również LNK2019. Plik nagłówkowy jest dołączony wszędzie, gdzie uważasz to za właściwe, ale są tylko funkcje śródwierszowe plik .cpp przejścia przez kompilator; w związku z tym konsolidator uznaje funkcji nierozpoznane obiekty zewnętrzne, gdy jest używana w innych modułach.

```
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

Następnie wyszukaj maszynę

```
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

Następnie wyszukaj maszynę

```
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