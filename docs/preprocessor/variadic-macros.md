---
title: Makra Wariadyczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5918c7d91a3568799f361fcb42edb2e9c7b1445e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850538"
---
# <a name="variadic-macros"></a>Makra wariadyczne
Makra Wariadyczne są makra przypominającej funkcji, które zawiera zmienną liczbę argumentów.  
  
## <a name="remarks"></a>Uwagi  
 Aby korzystać ze zmienną liczbą argumentów makra, wielokropka mogą być określone jako ostatni argument formalny w definicji makra i identyfikator zastępczy `__VA_ARGS__` może służyć do definicji Aby wstawić dodatkowe argumenty.  `__VA_ARGS__` zastępuje wszystkie argumenty, które odpowiada wielokropka umieszczaniu między nimi.  
  
 C Standard określa, że co najmniej jednego argumentu muszą być przekazywane do wielokropka, aby upewnić się, że makro nie odpowiada wyrażeniu zawierającym przecinek końcowy.  Implementacja Visual C++ spowoduje wyłączenie przecinek końcowy, jeżeli nie przekazano argumentów do wielokropka.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// variadic_macros.cpp  
#include <stdio.h>  
#define EMPTY  
  
#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }  
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }  
#define CHECK3(...) { printf(__VA_ARGS__); }  
#define MACRO(s, ...) printf(s, __VA_ARGS__)  
  
int main() {  
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");  
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print  
  
    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print  
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");  
  
    // always invokes printf in the macro  
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");  
  
    MACRO("hello, world\n");  
  
    MACRO("error\n", EMPTY); // would cause error C2059, except VC++   
                             // suppresses the trailing comma  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Makra (C/C++)](../preprocessor/macros-c-cpp.md)