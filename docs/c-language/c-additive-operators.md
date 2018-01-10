---
title: "Operatory dodawania języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 340aac3d3aab6951af43b824f1c8d0dd866f7a39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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