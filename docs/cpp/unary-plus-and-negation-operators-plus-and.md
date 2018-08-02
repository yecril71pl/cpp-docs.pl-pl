---
title: 'Operatory jednoargumentowe Plus i negacji: + i - | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 06e7f6bd089866619d82798bb220580e8a11b04b
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460896"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Operatory jednoargumentowe plus i negacji: + i -
## <a name="syntax"></a>Składnia  
  
```  
+ cast-expression  
- cast-expression  
```  
  
## <a name="-operator"></a>+ — Operator  
 Wynik Jednoargumentowy operator plus (**+**) to wartość swojego operandu. Argument operacji do Jednoargumentowy operator plus musi być typu arytmetycznego.  
  
 Promocja typu całkowitego odbywa się w przypadku argumentów operacji typu całkowitego. Wynikowy typ to typ, do którego argument jest podnoszony. W związku z tym, wyrażenie `+ch`, gdzie `ch` typu **char**, typ **int**; wartość pozostaje niezmieniona. Zobacz [konwersje standardowe](standard-conversions.md) uzyskać więcej informacji o jak jest wykonywane podwyższenia poziomu.  
  
## <a name="--operator"></a>- — Operator  
 Jednoargumentowy operator negacji (**-**) daje wartość negatywną swojego operandu. Argument operacji do Jednoargumentowy operator negacji musi być typu arytmetycznego.  
  
 Promocja typu całkowitego odbywa się w przypadku argumentów operacji typu całkowitego, a wynikowy typ jest typem, do którego argument jest podnoszony. Zobacz [konwersje standardowe](standard-conversions.md) Aby uzyskać więcej informacji na temat sposobu promowania jest wykonywane.  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Negacja Jednoargumentowa o ilości nieznaczonych odbywa się przez odjęcie wartości argumentu z 2 ^ n, gdzie n to liczba bitów w obiekcie o danym typie bez znaku.
  
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)