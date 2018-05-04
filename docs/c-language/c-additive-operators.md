---
title: Operatory dodawania języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df491508f7898fe3c97bc02a83e5259baa9c89f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="c-additive-operators"></a>Operatory dodawania języka C
Operatory dodawania wykonać dodawania (**+**) i odejmowanie (**-**).  
  
## <a name="syntax"></a>Składnia  
 *wyrażenie dodatku*:  
 *wyrażenia mnożenia*  
  
 *wyrażenie dodatku***+***wyrażenia mnożenia*   
  
 *wyrażenie dodatku***-***wyrażenia mnożenia*   
  
> [!NOTE]
>  Mimo że składnia *dodatku wyrażenie* obejmuje *wyrażenia mnożenia*, oznacza to, że wyrażenia mnożenia są wymagane. Zobacz składnię [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md), dla *wyrażenia mnożenia*, *wyrażenie cast*, i *wyrażenie jednoargumentowe*.  
  
 Argumenty operacji może być wartości całkowitą lub zmiennoprzecinkową. Niektóre operacje dodawania można również przeprowadzić na wartości wskaźników, zgodnie z dyskusji każdego operatora.  
  
 Operatory dodawania Wykonaj popularne konwersje arytmetyczne na argumentów całkowitych i zmiennoprzecinkowych. Typ wyniku jest typ operandy po konwersji. Ponieważ konwersje wykonywane przez operatorów dodawania nie zapewniają przepełnienie lub niedomiar warunków, informacje mogą zostać utracone, jeśli wynik operacji dodawania nie może być reprezentowany w typie operandy po konwersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory dodawania: + i -](../cpp/additive-operators-plus-and.md)