---
title: Typy wyliczeniowe (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d21a887c29b792b2857d0ee546dbc9722b60a264
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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