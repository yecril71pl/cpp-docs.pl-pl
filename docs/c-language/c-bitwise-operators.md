---
title: "Operatory bitowe języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3be1384c12ece809bd8fc275625efd4acef5a407
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-bitwise-operators"></a>Operatory bitowe języka C
Operatory bitowe wykonać bitowo- i (**&**), z bitowego OR wyłączne (**^**) i włącznie Alternatywy (**&#124;**) operacje.  
  
 **Składnia**  
  
 *I wyrażenia*:  
 *wyrażenie równości*  
  
 *Wyrażenia AND***&***wyrażenie równości*   
  
 *wyrażenie OR-wyłącznie*:  
 *Wyrażenia AND*  
  
 *wyrażenie OR-wyłącznie***^***i wyrażenia*   
  
 *wraz z wartościami granicznymi wyrażenie OR*:  
 *wyrażenie OR-na wyłączność*  
  
 *wraz z wartościami granicznymi wyrażenie OR* &#124; *wyłącznie OR-wyrażenie*  
  
 Argumenty operacji operatory bitowe muszą mieć typów całkowitych, ale ich typy mogą być różne. Popularne konwersje arytmetyczne; wykonywania tych operatorów Typ wyniku jest typ operandy po konwersji.  
  
 Operatory bitowe języka C są opisane poniżej:  
  
|Operator|Opis|  
|--------------|-----------------|  
|**&**|Operatory- i operatora porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli oba bity 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.|  
|**^**|Operatora bitowego OR wyłączne porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli jeden bit ma wartość 0, a inne bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.|  
|**&#124;**|Operator włącznie Alternatywy porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli albo bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.|  
  
## <a name="examples"></a>Przykłady  
 Deklaracje te są używane następujące trzy przykłady:  
  
```  
short i = 0xAB00;  
short j = 0xABCD;  
short n;  
  
n = i & j;  
```  
  
 Wynik przypisane do `n` w tym pierwszym przykładzie jest taka sama jak `i` (0xAB00 szesnastkowym).  
  
```  
n = i | j;  
  
n = i ^ j;  
```  
  
 Bitowe włącznie lub w drugim przykładzie powoduje wartość 0xABCD (szesnastkowo), podczas gdy lub operator wyłączny w trzecim przykładzie tworzy 0xCD (szesnastkowo).  
  
 **Dotyczące firmy Microsoft**  
  
 Wyniki operacji na liczb całkowitych ze znakiem jest zdefiniowane w implementacji zgodnie z ANSI C standard. Kompilator Microsoft C Operacje bitowe na liczb całkowitych ze znakiem praca taka sama jak operacje bitowe na liczb całkowitych bez znaku. Na przykład `-16 & 99` może zostać wyrażona w danych binarnych jako  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 Wynik iloczynu bitowego AND jest 96 dziesiętną.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowy Operator AND: &](../cpp/bitwise-and-operator-amp.md)   
 [Operator wyłączny sumy bitowej OR — Operator: ^](../cpp/bitwise-exclusive-or-operator-hat.md)   
 [Operator włącznie lub Operator: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)