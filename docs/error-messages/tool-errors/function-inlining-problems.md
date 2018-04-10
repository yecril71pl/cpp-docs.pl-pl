---
title: Problemy ze Śródwierszowaniem funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 97ffa56fc748eea8f65f5fe79c7a9defa7238f82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="function-inlining-problems"></a>Problemy ze śródwierszowaniem funkcji
Jeśli używasz ze śródwierszowaniem funkcji, należy:  
  
-   Ma wbudowane funkcje realizowane w pliku nagłówka, który zawiera.  
  
-   Ma ze śródwierszowaniem włączone w pliku nagłówka.  
  
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
  
 a następnie  
  
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
  
 Jeśli używasz `#pragma inline_depth` kompilatora dyrektywy, upewnij się, że masz wartość 2 lub większą. Wartość zero spowoduje wyłączenie ze śródwierszowaniem. Upewnij się, czy używasz również **/Ob1** lub **/ob2** — opcje kompilatora.  
  
 Mieszanie opcje kompilacji wbudowanego i z systemem innym niż wbudowany w różnych modułach czasami może powodować problemy. Jeśli biblioteka języka C++ tworzona jest włączona ze śródwierszowaniem funkcji ([/Ob1](../../build/reference/ob-inline-function-expansion.md) lub [/ob2](../../build/reference/ob-inline-function-expansion.md)), ale odpowiadający mu plik nagłówka opisujące funkcji ma ze śródwierszowaniem wyłączone (żadna opcja), wystąpi błąd LNK2001. Funkcje nie są wbudowane do kodu z pliku nagłówka, ale ponieważ nie są one plik biblioteki nie jest adres nie można rozpoznać odwołania.  
  
 Podobnie projekt, który korzysta ze śródwierszowaniem funkcji jeszcze definiuje funkcji w pliku .cpp, a nie w nagłówku pliku otrzymają również LNK2019. Plik nagłówka jest dołączony wszędzie uważasz to za właściwe, ale te funkcje są tylko wbudowanego pliku .cpp przejścia przez kompilator; w związku z tym konsolidator widzi funkcji jako nierozpoznane externals, gdy są używane w innych modułach.  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 a następnie  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 a następnie  
  
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