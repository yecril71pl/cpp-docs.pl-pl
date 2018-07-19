---
title: Operator noexcept (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/12/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noexcept_cpp
dev_langs:
- C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8eb8e6900dc12e4f176daf63bb711198f5e41429
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939292"
---
# <a name="noexcept-c"></a>noexcept (C++)
**C ++ 11:** Określa, czy funkcja może zgłaszać wyjątki.  
  
## <a name="syntax"></a>Składnia  
  
> *wyrażenie noexcept*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**Operator noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**Operator noexcept (** *wyrażenie_stałe* **)**  
  
### <a name="parameters"></a>Parametry  
 *constant-expression*  
 Wyrażenie stałe typu **bool** reprezentujący, czy zestaw typów wyjątków potencjalnych jest pusty. Bezwarunkowe wersja jest odpowiednikiem `noexcept(true)`.  
  
## <a name="remarks"></a>Uwagi  
 A *wyrażenie noexcept* jest rodzajem z *Specyfikacja wyjątku*, sufiks do deklaracji funkcji, które reprezentuje zestaw typów, które mogą towarzyszyć każdy wyjątek, który kończy działanie aparatu obsługi wyjątków Funkcja. Jednoargumentowy operator warunkowy `noexcept(` *constant_expression* `)` gdzie *constant_expression* yeilds **true**, a jej bezwarunkowe synonim `noexcept`, określić, że zestaw potencjalnych typy wyjątków, które można zakończyć działanie funkcji jest pusta. Oznacza to funkcja nigdy nie zgłasza wyjątek i nigdy nie zezwala na wyjątek dotyczący propagowane poza zakres. Operator `noexcept(` *constant_expression* `)` gdzie *constant_expression* yeilds **false**, lub brak Specyfikacja wyjątku (inne niż dla funkcji destruktora lub dezalokacji), oznacza to, że zestaw potencjalne wyjątki, które można zakończyć działanie funkcji jest zbiór wszystkich typów.  
 
 Oznacz funkcję jako `noexcept` tylko wtedy, gdy wszystkie funkcje, które wywołuje, bezpośrednio lub pośrednio, są również `noexcept` lub **const**. Kompilator nie sprawdza co ścieżka kodu do obsługi wyjątków, które być może będą się pojawiać do `noexcept` funkcji. Jeśli wyjątek wyjść zewnętrznym zakresie funkcji oznaczonej `noexcept`, [std::terminate](../standard-library/exception-functions.md#terminate) jest wywoływana bezpośrednio, a nie ma żadnej gwarancji, że zostaną wywołane destruktory wszystkich obiektów w zakresie. Użyj `noexcept` zamiast specyfikatora wyjątków dynamicznych `throw()`, który jest już przestarzały w standardzie. Zaleca się, należy zastosować `noexcept` dowolnej funkcji, które nigdy nie zezwala na wyjątek do propagowania na górę stosu wywołań. Gdy funkcja jest zadeklarowana `noexcept`, umożliwia kompilatorowi generowanie kodu bardziej wydajne w kilku różnych kontekstach. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków](exception-specifications-throw-cpp.md).   
  
## <a name="example"></a>Przykład  
Funkcja szablonu, który kopiuje jej argument może być zadeklarowana `noexcept` pod warunkiem, że obiekt, w której są kopiowane jest zwykłe stare dane typu (POD). Taka funkcja może być zadeklarowane następująco:  
  
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