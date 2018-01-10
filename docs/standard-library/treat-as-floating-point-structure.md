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
ms.workload: cplusplus
ms.openlocfilehash: 1679f6819da685a2c49587d703659b941bf45db6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

