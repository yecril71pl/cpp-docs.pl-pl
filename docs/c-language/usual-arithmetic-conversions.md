---
title: Popularne konwersje arytmetyczne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 66736e9b131725475d6f10f4a332edaa980a54f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="usual-arithmetic-conversions"></a>Popularne konwersje arytmetyczne
Większość operatorów C wykonywania konwersji typu można wyświetlić operandy wyrażenia na wspólny typ, albo aby rozszerzyć krótkich wartości rozmiar całkowitą w operacjach maszyny. Konwersje wykonywane przez operatorów C zależy od określonego operatora i typu argumentu lub argumentów operacji. Jednak wielu operatorów wykonywać podobne konwersje typów całkowitych i zmiennoprzecinkowych argumentów operacji. Konwersje te są określane jako "konwersje arytmetyczne." Konwersja wartości operandu na zgodne z typem nie powoduje żadnych zmian, jego wartość.  
  
 Konwersje arytmetyczne podsumowano poniżej są nazywane "popularne konwersje arytmetyczne." Te kroki są stosowane tylko w przypadku operatorów binarnych, w których jest oczekiwany typ arytmetyczny. Celem jest uzyskanie wspólny typ, który jest również typ wyniku. Aby ustalić, które konwersje rzeczywiście została wykonana, kompilator dotyczy następującego algorytmu operacji binarnych w wyrażeniu. Poniższe kroki nie są kolejność pierwszeństwa.  
  
1.  Jeśli którykolwiek argument operacji jest typu `long double`, drugiego operandu jest konwertowana na typ `long double`.  
  
2.  Jeśli nie jest spełniony warunek powyżej i albo operand jest typu **podwójne**, drugiego operandu jest konwertowana na typ **podwójne**.  
  
3.  Jeśli powyższe dwa warunki nie są spełnione, a albo operand jest typu **float**, drugiego operandu jest konwertowana na typ **float**.  
  
4.  Jeśli powyższe trzy warunki nie są spełnione (Brak argumenty operacji są typy zmiennoprzecinkowe), a następnie konwersje wartości całkowitych są wykonywane na operandów w następujący sposób:  
  
    -   Jeśli którykolwiek argument operacji jest typu `unsigned long`, drugiego operandu jest konwertowana na typ `unsigned long`.  
  
    -   Jeśli nie jest spełniony warunek powyżej i albo operand jest typu **długi** i drugą typu `unsigned int`, obydwa argumenty operacji są konwertowane na typ `unsigned long`.  
  
    -   Jeśli nie są spełnione dwa powyższe warunki, a albo operand jest typu **długi**, drugiego operandu jest konwertowana na typ **długi**.  
  
    -   Jeśli powyższe trzy warunki nie są spełnione, a albo operand jest typu `unsigned int`, drugiego operandu jest konwertowana na typ `unsigned int`.  
  
    -   Jeśli żaden z powyższych warunków nie jest spełniony, obydwa argumenty operacji są konwertowane na typ `int`.  
  
 Poniższy kod ilustruje te reguły konwersji:  
  
```  
float   fVal;  
double  dVal;  
int   iVal;  
unsigned long ulVal;  
  
dVal = iVal * ulVal; /* iVal converted to unsigned long  
                      * Uses step 4.  
                      * Result of multiplication converted to double   
                      */  
dVal = ulVal + fVal; /* ulVal converted to float  
                      * Uses step 3.  
                      * Result of addition converted to double   
                      */   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory języka C](../c-language/c-operators.md)