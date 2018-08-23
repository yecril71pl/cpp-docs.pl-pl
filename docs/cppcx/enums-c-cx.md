---
title: Typy wyliczeniowe (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 725e2b9edb7ba2a84418e900ffb1aafe4c5064af
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593967"
---
# <a name="enums-ccx"></a>Typy wyliczeniowe (C + +/ CX)
C + +/ CX obsługuje `public enum class` — słowo kluczowe, czyli analagous do standardowego języka C++ `scoped  enum`. Kiedy używasz moduł wyliczający, który jest zadeklarowana za pomocą `public enum class` — słowo kluczowe, musi być identyfikatorem wyliczenia zakresu z każdą wartość modułu wyliczającego.  
  
### <a name="remarks"></a>Uwagi  
 A `public enum class` , która nie ma specyfikatora dostępu, takich jak `public`, jest traktowany jako standard C++ [zakresie](../cpp/enumerations-cpp.md).  
  
 A `public enum class` lub `public enum struct` deklaracja może mieć typu podstawowego typu całkowitego, mimo że środowisko wykonawcze Windows wymaga typu int32 lub uint32 dla wyliczenia flag. Następująca składnia opisuje części `public enum class` lub `public enum struct`.  
  
 Ten przykład pokazuje, jak zdefiniować klasę publicznym typie wyliczeniowym:  
  
 [!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]  
  
 To Następny przykład pokazuje sposób wykorzystywania go:  
  
 [!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]  
  
### <a name="examples"></a>Przykłady  
 W następnych przykładach pokazano, jak zadeklarować wyliczenia  
  
 [!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]  
  
 Następny przykład pokazuje, jak Rzutowanie na odpowiedniki liczbowych i wykonywać porównania. Należy zauważyć, że użycie modułu wyliczającego `One` jest objęte zakresem `Enum1` identyfikatorem wyliczenia, a moduł wyliczający `First` jest objęte zakresem `Enum2`.  
  
 [!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)