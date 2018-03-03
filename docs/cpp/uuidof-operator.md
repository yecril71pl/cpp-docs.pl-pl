---
title: __uuidof operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs:
- C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5d83f99b40e6eb897212fbcfb03c01b4f6b55e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="uuidof-operator"></a>Operator __uuidof
**Dotyczące firmy Microsoft**  
  
 Pobiera identyfikator GUID dołączony do wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie* może być nazwa typu, wskaźnik, odwołanie lub tablicy tego typu, szablon specjalizowany w tych typów lub zmienną z tych typów. Argument jest prawidłowy, jak kompilator służy można znaleźć dołączonego identyfikatora GUID.  
  
 Jest szczególnych przypadkach tym wewnętrznych, gdy albo **0** lub **NULL** jest podana jako argument. W takim przypadku `__uuidof` zwraca identyfikator GUID składa się z zer.  
  
 Użyj słowa kluczowego można wyodrębnić identyfikatora GUID dołączony do:  
  
-   Obiekt o [uuid](../cpp/uuid-cpp.md) rozszerzonych atrybutów.  
  
-   Blok biblioteki utworzone za pomocą [modułu](../windows/module-cpp.md) atrybutu.  
  
> [!NOTE]
>  W kompilację debugowania `__uuidof` zawsze inicjuje obiekt dynamicznie (w czasie wykonywania). W kompilacji wydania `__uuidof` statycznie (w czasie kompilacji) można zainicjować obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod (skompilowane z ole32.lib) do wyświetlenia identyfikatora uuid bloku biblioteki utworzone za pomocą atrybutu modułu:  
  
```  
// expre_uuidof.cpp  
// compile with: ole32.lib  
#include "stdio.h"  
#include "windows.h"  
  
[emitidl];  
[module(name="MyLib")];  
[export]  
struct stuff {  
   int i;  
};  
  
int main() {  
   LPOLESTR lpolestr;  
   StringFromCLSID(__uuidof(MyLib), &lpolestr);  
   wprintf_s(L"%s", lpolestr);  
   CoTaskMemFree(lpolestr);  
}  
```  
  
## <a name="comments"></a>Komentarze  
 W przypadkach, gdy nazwa biblioteki nie jest już w zakresie, można użyć __LIBID\_ zamiast `__uuidof`. Na przykład:  
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)