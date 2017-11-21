---
title: "treat_as_floating_point — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: chrono/std::chrono::treat_as_floating_point
dev_langs: C++
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8bfdda5bab6db19a1cf6d123f141f87249b62478
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point — Struktura
Określa, czy `Rep` może być traktowana jako typ zmiennoprzecinkowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Rep>  
struct treat_as_floating_point : is_floating_point<Rep>;  
```  
  
## <a name="remarks"></a>Uwagi  
 `Rep`może być traktowana jako typ zmiennoprzecinkowy tylko wtedy, gdy specjalizacji `treat_as_floating_point<Rep>` jest pochodną [true_type](../standard-library/type-traits-typedefs.md#true_type). Klasy szablonu może być specjalizowany dla typu zdefiniowanego przez użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<chrono >  
  
 **Namespace:** std::chrono  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono >](../standard-library/chrono.md)

