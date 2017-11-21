---
title: '&lt;limity&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 1b69623aa9eccfca57667d4f33546512799b172f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltlimitsgt-enums"></a>&lt;limity&gt; wyliczenia
|||  
|-|-|  
|[float_denorm_style](#float_denorm_style)|[float_round_style](#float_round_style)|  
  
##  <a name="float_denorm_style"></a>float_denorm_style — wyliczenie  
 Wyliczenie zawiera opis różnych metod, które można wybrać implementację reprezentujący nieznormalizowany wartość zmiennoprzecinkowa — jeden za mały, aby reprezentować znormalizowaną wartość:  
  
```
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wyliczenie:  
  
- **denorm_indeterminate** Jeśli obecności lub braku nieznormalizowany formularzy nie można określić podczas tłumaczenia.  
  
- **denorm_absent** Jeśli nieznormalizowany formularze są nieobecne.  
  
- **denorm_present** Jeśli nieznormalizowany formularze są obecne.  
  
### <a name="example"></a>Przykład  
  Zobacz [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm) na przykład, w którym mogą być używane wartości tego wyliczenia.  
  
##  <a name="float_round_style"></a>float_round_style — wyliczenie  
 Wyliczenie zawiera opis różnych metod, które można wybrać implementację zaokrąglania wartości zmiennoprzecinkowej na wartość całkowitą.  
  
```
enum float_round_style {    
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wyliczenie:  
  
- **round_indeterminate** , jeśli nie można określić metody zaokrąglania.  
  
- **round_toward_zero** Jeśli round w kierunku zera.  
  
- **round_to_nearest** Jeśli zaokrąglona do najbliższej liczby całkowitej.  
  
- **round_toward_infinity** Jeśli round w kierunku od zera.  
  
- **round_toward_neg_infinity** Jeśli zaokrąglona do bardziej ujemnej liczby całkowitej.  
  
### <a name="example"></a>Przykład  
  Zobacz [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) na przykład, w którym mogą być używane wartości tego wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [\<limity >](../standard-library/limits.md)



