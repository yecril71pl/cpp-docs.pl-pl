---
title: '&lt;ostream&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs: C++
helpviewer_keywords: ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4805086fb3d63d16f5f9ce6bf3b9e900b436569
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;
Definiuje klasę szablonu [basic_ostream —](../standard-library/basic-ostream-class.md), która przekazuje wstawienia dla iostream. Nagłówek definiuje również kilka manipulatory pokrewne. (Ten nagłówek jest zwykle dołączone dla Ciebie przez inną nagłówków iostream. Rzadko należy dołączyć go bezpośrednio.)  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <ostream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Tworzy typ z `basic_ostream` które jest przeznaczone na `char` i `char_traits` specjalne na `char`.|  
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Tworzy typ z `basic_ostream` które jest przeznaczone na `wchar_t` i `char_traits` specjalne na `wchar_t`.|  
  
### <a name="manipulators"></a>Manipulatory  
  
|||  
|-|-|  
|[endl](../standard-library/ostream-functions.md#endl)|Przerywa wiersza i opróżnia bufor.|  
|[kończy się](../standard-library/ostream-functions.md#ends)|Kończy się ciągiem.|  
|[Flush](../standard-library/ostream-functions.md#flush)|Opróżnia bufor.|  
|[swap](../standard-library/ostream-functions.md#swap)|Zamienia wartości po lewej stronie `basic_ostream` obiekt parametru do tych praw `basic_ostream` obiekt parametru.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[Operator <<](../standard-library/ostream-operators.md#op_lt_lt)|Zapisuje różnych typów w strumieniu.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[basic_ostream —](../standard-library/basic-ostream-class.md)|Klasy szablonów opisano obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych w buforze strumienia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



