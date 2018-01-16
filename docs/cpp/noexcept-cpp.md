---
title: noexcept (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/12/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noexcept_cpp
dev_langs: C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b78c19cb156312b6087b75e50c0e0fa28a00246
ms.sourcegitcommit: c2e990450ccd528d85b2783fbc63042612987cfd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="noexcept-c"></a>noexcept (C++)
**C ++ 11:** Określa, czy funkcja może zgłaszać wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
> *wyrażenie noexcept*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept (** *wyrażenia* **)**  
  
### <a name="parameters"></a>Parametry  
 *constant-expression*  
 Wyrażenie stałe typu `bool` reprezentujący czy zestaw potencjalnych typów wyjątków jest pusta. Bezwarunkowe wersji jest odpowiednikiem `noexcept(true)`.  
  
## <a name="remarks"></a>Uwagi  
 A *wyrażenie noexcept* jest rodzajem elementu *specyfikacji wyjątku*, sufiks do deklaracji funkcji, która reprezentuje zestaw typów zgodnych przez obsługę wyjątków dla wszelkich wyjątek, który zamyka Funkcja. Jednoargumentowy operator warunkowy `noexcept(` *constant_expression* `)` gdzie *constant_expression* yeilds `true`, a jej bezwarunkowe synonim `noexcept`, Określ, czy zestaw potencjalnych typów wyjątków, które można zakończyć działanie funkcji jest pusta. Oznacza to, że funkcja nigdy nie zgłasza wyjątek i nigdy nie umożliwia wyjątek propagację poza jej zakres. Operator `noexcept(` *constant_expression* `)` gdzie *constant_expression* yeilds `false`, lub Brak specyfikacji wyjątku (innych niż dla Funkcja destruktora lub dezalokacji), wskazuje, że zestaw potencjalnych wyjątki, które można zakończyć działanie funkcji jest zestaw wszystkich typów.  
 
 Oznacz jako funkcję `noexcept` tylko wtedy, gdy wszystkie funkcje, które wywołuje, bezpośrednio lub pośrednio, są również `noexcept` lub `const`. Kompilator nie sprawdza co ścieżka kodu dla wyjątków, które mogą bąbelkowy do `noexcept` funkcji. Jeśli wyjątek zakończyć zewnętrznym zakresie funkcji oznaczone `noexcept`, [std::terminate](../standard-library/exception-functions.md#terminate) jest wywoływana natychmiast, i nie ma żadnej gwarancji, zostanie wywołany destruktory wszystkie obiekty w zasięgu. Użyj `noexcept` zamiast specyfikator wyjątków dynamicznych `throw()`, która jest teraz przestarzałe w standardzie. Firma Microsoft zaleca, należy zastosować `noexcept` dowolnej funkcji, które nigdy nie umożliwia wyjątek propagowany aż stosu wywołań. Gdy funkcja jest zadeklarowany jako `noexcept`, umożliwia kompilatorowi generowanie kodu efektywniejsze w kilku różnych kontekstach. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków](exception-specifications-throw-cpp.md).   
  
## <a name="example"></a>Przykład  
Funkcja szablonu, który kopiuje jej argument może być zadeklarowana `noexcept` pod warunkiem, że obiekt kopiowane jest zwykły stary typ danych (POD). Tych funkcji można zadeklarować następująco:  
  
```cpp  
#include <type_traits>  
  
template <typename T>  
T copy_object(const T& obj) noexcept(std::is_pod<T>)  
{  
   // ...   
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków języka C++](cpp-exception-handling.md) [specyfikacje wyjątków (throw, noexcept)](exception-specifications-throw-cpp.md)