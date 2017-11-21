---
title: "Konwersje z typów zmiennoprzecinkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4974edd25d0fcdd8d990b60459517bb1148c74ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-from-floating-point-types"></a>Konwersje z typów zmiennoprzecinkowych
A **float** konwertowane na wartość **podwójne** lub `long double`, lub **podwójne** przekonwertować `long double`, ulega ma zmiany w wartości. A **podwójne** konwertowane na wartość **float** wartość jest reprezentowany dokładnie, jeśli to możliwe. Dokładność mogą zostać utracone, jeśli wartość nie może być reprezentowany dokładnie. Jeśli wynik jest poza zakresem, zachowanie jest niezdefiniowany. Zobacz [limity dla stałych Floating-Point](../c-language/limits-on-floating-point-constants.md) dla typów zmiennoprzecinkowych.  
  
 Wartość zmiennoprzecinkowa jest konwertowana na wartością całkowitą, konwertując pierwszy **długi**, następnie z **długi** wartość określoną wartość całkowitą. Część zmiennej wartości zostaną odrzucone podczas konwersji do **długi**. Jeśli wynik nadal jest zbyt duży, aby zmieścić w **długi**, wynik konwersji jest niezdefiniowany.  
  
 **Dotyczące firmy Microsoft**  
  
 Podczas konwertowania **podwójne** lub `long double` liczba zmiennoprzecinkowa do mniejsza liczba zmiennoprzecinkowa, wartość zmiennej liczb zmiennoprzecinkowych zostały obcięte kierunku zera po wystąpieniu niedopełnienie. Przepełnienie powoduje błąd w czasie wykonywania. Należy pamiętać, że kompilator Microsoft C mapuje `long double` na typ **podwójne**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Poniższa tabela zawiera podsumowanie konwersje z typów zmiennoprzecinkowych.  
  
### <a name="conversions-from-floating-point-types"></a>Konwersje z typów zmiennoprzecinkowych  
  
|Z|Do|Metoda|  
|----------|--------|------------|  
|**float**|`char`|Konwertuj na **długi**; przekonwertować **długi** do`char`|  
|**float**|**krótki**|Konwertuj na **długi**; przekonwertować **długi** do **krótki**|  
|**float**|**długa**|Obciąć po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długi**, wynikiem jest niezdefiniowany.|  
|**float**|**short bez znaku**|Konwertuj na **długi**; przekonwertować **długi** do `unsigned` **krótki**|  
|**float**|`unsigned long`|Konwertuj na **długi**; przekonwertować **długi** do `unsigned` **długa**|  
|**float**|**podwójne**|Zmień reprezentacji wewnętrznej|  
|**float**|`long double`|Zmień reprezentacji wewnętrznej|  
|**podwójne**|`char`|Konwertuj na **float**; przekonwertować **float** do`char`|  
|**podwójne**|**krótki**|Konwertuj na **float**; przekonwertować **float** do **krótki**|  
|**podwójne**|**długa**|Obciąć po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długi**, wynikiem jest niezdefiniowany.|  
|**podwójne**|**short bez znaku**|Konwertuj na **długi**; przekonwertować **długi** do **krótko bez znaku**|  
|**podwójne**|`unsigned long`|Konwertuj na **długi**; przekonwertować **długi** do `unsigned` **długa**|  
|**podwójne**|**float**|Reprezentuje jako **float**. Jeśli **podwójne** wartość nie może być reprezentowany dokładnie jako **float**, utrata dokładności. Jeśli wartość jest za duży, może być reprezentowana jako **float**, wynikiem jest niezdefiniowany.|  
|`long double`|`char`|Konwertuj na **float**; przekonwertować **float** do`char`|  
|`long double`|**krótki**|Konwertuj na **float**; przekonwertować **float** do **krótki**|  
|`long double`|**długa**|Obciąć po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długi**, wynikiem jest niezdefiniowany.|  
|`long double`|**short bez znaku**|Konwertuj na **długi**; przekonwertować **długi** do `unsigned` **krótki**|  
|`long double`|`unsigned long`|Konwertuj na **długi**; przekonwertować **długi** do `unsigned` **długa**|  
|`long double`|**float**|Reprezentuje jako **float**. Jeśli **podwójne** wartość nie może być reprezentowany dokładnie jako **float**, utrata dokładności. Jeśli wartość jest za duży, może być reprezentowana jako **float**, wynikiem jest niezdefiniowany.|  
|`long double`|**podwójne**|**Podwójnej długości** wartość jest traktowana jako **podwójne**.|  
  
 Konwersje z **float**, **podwójne**, lub `long double` wartości do `unsigned long` nie są dokładne, jeśli wartość konwertowanej jest większa niż maksymalna dodatnich **long**wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje przypisań](../c-language/assignment-conversions.md)