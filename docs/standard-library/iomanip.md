---
title: "&lt;iomanip —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
dev_langs: C++
helpviewer_keywords: iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c2f229f5706902eac1c0326cfb446b4dc650c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltiomanipgt"></a>&lt;iomanip —&gt;
Obejmują `iostreams` standardowy nagłówek `<iomanip>` do definiowania kilka manipulatory każdy wykonać jeden argument.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <iomanip>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Zwraca każdy z tych manipulatory nieokreślonego typu o nazwie **T1** za pośrednictwem **T10**, który zarówno overloads `basic_istream` \< **elementu**, **Tr**>`::`[operator >>](../standard-library/istream-operators.md#op_gt_gt) i `basic_ostream` \< **elementu**, **Tr** > `::` [operator <<](../standard-library/ostream-operators.md#op_lt_lt).  
  
### <a name="manipulators"></a>Manipulatory  
  
|||  
|-|-|  
|[get_money —](../standard-library/iomanip-functions.md#iomanip_get_money)|Uzyskuje kwotę pieniężną, opcjonalnie w formacie międzynarodowej.|  
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Pobiera czas w strukturze czasu przy użyciu określonego formatu.|  
|[put_money —](../standard-library/iomanip-functions.md#iomanip_put_money)|Udostępnia pieniężnego, opcjonalnie w formacie międzynarodowej.|  
|[put_time —](../standard-library/iomanip-functions.md#iomanip_put_time)|Miejsce na godzinę w strukturze czasu i ciąg formatu do użycia.|  
|[w cudzysłowach](../standard-library/iomanip-functions.md#quoted)|Umożliwia wygodne dwustronną komunikację ciągów z operatorów wstawiania i wyodrębniania.|  
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Usuwa określone flagi.|  
|[setbase](../standard-library/iomanip-functions.md#setbase)|Ustaw podstawowej liczb całkowitych.|  
|[setfill](../standard-library/iomanip-functions.md#setfill)|Ustawia znak używany do wypełniania miejsc w prawej strony ekranu.|  
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Ustawia określone flagi.|  
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Ustawia dokładność wartości zmiennoprzecinkowych.|  
|[setw](../standard-library/iomanip-functions.md#setw)|Określa szerokość pola wyświetlania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



