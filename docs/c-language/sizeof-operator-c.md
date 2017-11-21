---
title: sizeof Operator (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sizeof
dev_langs: C++
helpviewer_keywords: sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 11fa4acae05c5488ce1d90873ec816744c7e83df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sizeof-operator-c"></a>sizeof — operator (C)
Operator `sizeof` podaje ilość pamięci w bajtach, wymaganą do przechowywania obiektu typu operand. Ten operator umożliwia Unikaj określania rozmiarów maszyny zależne od danych w programach.  
  
## <a name="syntax"></a>Składnia  
  
```  
sizeof unary-expression  
sizeof ( type-name )  
```  
  
## <a name="remarks"></a>Uwagi  
Argument jest albo identyfikatora, który jest *wyrażenie jednoargumentowe*, lub wyrażeniem rzutowania typów (to znaczy specyfikatora typu w nawiasach). *Wyrażenie jednoargumentowe* nie może reprezentować obiekt pola bitowego, niekompletnego typu lub oznaczeniem funkcji. Wynik jest nieoznaczoną stałą całkowitą. Standardowy nagłówek STDDEF. H definiuje tego typu jako **size_t**.  
  
Po zastosowaniu operatora `sizeof` do identyfikatora tablicy, wynik jest rozmiarem całej tablicy, a nie rozmiarem wskaźnika reprezentowanego przez identyfikator tablicy.  
  
Po zastosowaniu operatora `sizeof` do nazwy typu struktury lub unii lub identyfikatora typu struktury lub unii, wynik jest liczbą bajtów w strukturze lub unii, w tym wypełnieniem wewnętrznym i końcowym. Ten rozmiar może obejmować wypełnienie wewnętrzne i końcowe używane do dostosowywania elementów członkowskich struktury lub unii w granicach pamięci. Jednakże, wynik może nie odpowiadać wielkości obliczonej przez dodanie pamięci wymaganej przez poszczególne elementy członkowskie.  
  
Jeśli tablica bez określonego rozmiaru jest ostatnim elementem struktury, operator `sizeof` zwróci rozmiar struktury bez tablicy.  
  
```  
buffer = calloc(100, sizeof (int) );  
```  
  
W poniższym przykładzie użyto operatora `sizeof` do przekazania rozmiaru `int`, który waha się między maszynami, jako argumentu funkcji czasu wykonywania o nazwie `calloc`. Wartość zwracana przez funkcję jest przechowywana w `buffer`.  
  
```  
static char *strings[] = {  
      "this is string one",  
      "this is string two",  
      "this is string three",  
   };  
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );   
```  
  
W tym przykładzie `strings` jest tablicą wskaźników do `char`. Liczbą wskaźników jest liczba elementów w tablicy, ale nie jest ona określona. Łatwo jest określić liczbę wskaźników za pomocą operatora `sizeof`, aby obliczyć liczbę elementów w tablicy. **Const** całkowitą `string_no` zainicjowano do tego numeru. Ponieważ jest on **const** wartość `string_no` nie może być modyfikowany.  
  
## <a name="see-also"></a>Zobacz też  
[Operatory języka C](c-operators.md)  
[Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  