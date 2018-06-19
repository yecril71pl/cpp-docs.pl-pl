---
title: Typy wyliczeniowe (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c96fa4e7194e262eec0be4cf5f7467c163530bd2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087384"
---
# <a name="enums-ccx"></a>Typy wyliczeniowe (C + +/ CX)
C + +/ CX obsługuje `public enum class` — słowo kluczowe, czyli analagous do standardu C++ `scoped  enum`. Jeśli używasz moduł wyliczający, który jest zadeklarowana przy użyciu `public enum class` — słowo kluczowe, musisz użyć identyfikator wyliczenia, aby zakres wartości modułu wyliczającego.  
  
### <a name="remarks"></a>Uwagi  
 A `public enum class` który nie ma specyfikatora dostępu, takich jak `public`, jest traktowany jako standard C++ [zakres wyliczenia](../cpp/enumerations-cpp.md).  
  
 A `public enum class` lub `public enum struct` deklaracja może mieć typu podstawowego typu całkowitego, mimo że środowisko wykonawcze systemu Windows, sama wymaga typu int32 lub uint32 dla wyliczenia flag. Następująca składnia opisano części `public enum class` lub `public enum struct`.  
  
 W tym przykładzie pokazano, jak zdefiniować klasę publicznym typie wyliczeniowym:  
  
 [!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]  
  
 Ten następnym przykładzie pokazano, jak pobrać go:  
  
 [!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]  
  
### <a name="examples"></a>Przykłady  
 Następny przykładach pokazano, jak można zadeklarować wyliczenia  
  
 [!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]  
  
 Kolejnym przykładzie pokazano, jak rzutować odpowiedniki numeryczne i wykonywać porównania. Należy zauważyć, że użycie modułu wyliczającego `One` ograniczone w zależności od `Enum1` identyfikator wyliczenia i modułu wyliczającego `First` ograniczone w zależności od `Enum2`.  
  
 [!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)