---
title: _ITERATOR_DEBUG_LEVEL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _ITERATOR_DEBUG_LEVEL
dev_langs: C++
helpviewer_keywords: _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 14939c7c39d207e686bcccf786dcabf93e809059
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL
`_ITERATOR_DEBUG_LEVEL` Makro kontrolek czy [zaznaczone Iteratory](../standard-library/checked-iterators.md) i [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md) są włączone. To makro zastępuje i łączą funkcjonalność starszej `_SECURE_SCL` i `_HAS_ITERATOR_DEBUGGING` makra.  
  
## <a name="macro-values"></a>Wartości — makro  
W poniższej tabeli przedstawiono możliwe wartości `_ITERATOR_DEBUG_LEVEL` makra.  
  
|Tryb kompilacji|Wartość makra|Opis|  
|----------------------|----------------|-----------------|  
|**Debugowania**|||  
||0|Wyłącza zaznaczone Iteratory i wyłącza debugowania iteratora.|  
||1|Zaznaczone Iteratory włącza i wyłącza debugowania iteratora.|  
||2 (ustawienie domyślne)|Włącza iteratora debugowania. zaznaczone Iteratory nie są istotne.|  
|**Wersja**|||  
||0 (ustawienie domyślne)|Wyłącza zaznaczone Iteratory.|  
||1|Włącza zaznaczone Iteratory; debugowania iteratora nie jest ważna.|  
  
W trybie wersji kompilator generuje błąd, jeśli określono `_ITERATOR_DEBUG_LEVEL` 2.  
  
## <a name="remarks"></a>Uwagi  
`_ITERATOR_DEBUG_LEVEL` Makro kontrolek czy [zaznaczone Iteratory](../standard-library/checked-iterators.md) są włączone i w trybie debugowania, czy [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md) jest włączona. Jeśli `_ITERATOR_DEBUG_LEVEL` jest zdefiniowany jako zaznaczone Iteratory 1 lub 2, upewnij się, czy granice kontenerów nie zostaną zastąpione. Jeśli `_ITERATOR_DEBUG_LEVEL` wynosi 0, Iteratory nie są sprawdzane. Gdy `_ITERATOR_DEBUG_LEVEL` jest zdefiniowany jako 1, wszelkie przyczyny użycie niebezpieczny iteratora błąd w czasie wykonywania i program zostanie zakończony. Gdy `_ITERATOR_DEBUG_LEVEL` jest zdefiniowany jako 2, przyczyny użycie niebezpieczny iteratora assert i okno dialogowe błąd środowiska uruchomieniowego, które umożliwia przerwanie w debugerze. 

Ponieważ `_ITERATOR_DEBUG_LEVEL` makro obsługuje funkcje podobne do `_SECURE_SCL` i `_HAS_ITERATOR_DEBUGGING` makra, może być wiedzą które makro i makra wartość do użycia w danej sytuacji. Aby uniknąć pomyłek, zalecane jest użycie tylko `_ITERATOR_DEBUG_LEVEL` makra. Poniższa tabela zawiera opis odpowiednikiem `_ITERATOR_DEBUG_LEVEL` makro wartość używaną dla różnych wartości `_SECURE_SCL` i `_HAS_ITERATOR_DEBUGGING` w istniejącym kodzie.  
  
|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (wartość domyślna wersja)|0 (wyłączone)|0 (wyłączone)|
|1|1 (włączone)|0 (wyłączone)|
|2 (wartość domyślna debugowania)|(nie dotyczy)|1 (włączone w trybie debugowania)|
  
Aby uzyskać informacje na temat sposobu Wyłącz ostrzeżenia o zaznaczone Iteratory, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
### <a name="example"></a>Przykład  
  
Aby określić wartość dla `_ITERATOR_DEBUG_LEVEL` makra, należy użyć [/D](../build/reference/d-preprocessor-definitions.md) opcję kompilatora, aby zdefiniować ją w wierszu polecenia, lub użyj `#define` przed standardowa biblioteka C++ nagłówki znajdują się w plikach źródłowych. Na przykład, w wierszu polecenia, aby skompilować *sample.cpp* w trybie debugowania i użyj Obsługa iteratora debugowania, możesz określić `_ITERATOR_DEBUG_LEVEL` definicji makra:  
  
`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`  
  
W pliku źródłowym Określ makro przed wszelkie nagłówki standardowa biblioteka, które definiują Iteratory.  
  
```cpp  
// sample.cpp  
  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
  
// ...
```  
  
## <a name="see-also"></a>Zobacz też  
[Zaznaczone Iteratory](../standard-library/checked-iterators.md)   
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)   
[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)
