---
title: 'Jednoargumentowe Plus i negacji operatory: + i - | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1441337275ac07b0d1ba39e8bfa34e7165f87f82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="unary-plus-and-negation-operators--and--"></a>Operatory jednoargumentowe plus i negacji: + i -
## <a name="syntax"></a>Składnia  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
```  
  
## <a name="-operator"></a>+ — Operator  
 Wynik jednoargumentowe plus — operator (**+**) to wartość jej argument. Argument jednoargumentowe plus operatora musi być typu arytmetycznego.  
  
 Promocję typu całkowitego odbywa się na całkowite argumentów operacji. Wynikowy typ jest typem, do którego zostanie podniesiona argument. W związku z tym wyrażenie `+ch`, gdzie `ch` jest typu `char`, zwraca typ `int`; wartość pozostaje niezmieniona. Zobacz [konwersje standardowe](standard-conversions.md) uzyskać więcej informacji o jak jest wykonywane podwyższenia poziomu.  
  
## <a name="--operator"></a>- — Operator  
 Jednoargumentowy operator negacji (**-**) tworzy ujemnego jej argument. Argument operacji do Jednoargumentowy operator negacji musi być typ arytmetyczny.  
  
 Promocję typu całkowitego odbywa się na całkowite argumentów operacji, a wynikowy typ jest typem, do którego zostanie podniesiona argument. Zobacz [konwersje standardowe](standard-conversions.md) uzyskać więcej informacji o realizację podwyższenia poziomu.  
  
## <a name="microsoft-specific"></a>Określone firmy Microsoft  
 Jednoargumentowy negacji niepodpisane ilości odbywa się przez odjęcie wartości argumentu z 2 ^ n, gdzie n to liczba bitów w obiekt danego typu bez znaku.
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
