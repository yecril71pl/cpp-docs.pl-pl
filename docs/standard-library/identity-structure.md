---
title: "Identity — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: utility/std::identity
dev_langs: C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 280ce6a24e1de9d0e7206e7f9e5b0d896d8c6787
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="identity-structure"></a>identity — Struktura
Struktury, zapewniająca definicją typu jako parametru szablonu.  
  
## <a name="syntax"></a>Składnia  
```  
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };  
```  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Wartość do identyfikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa zawiera definicję typu publicznego `type`, który jest taki sam jak typ parametru szablonu. Jest on używany w połączeniu z funkcją szablonu [do przodu](../standard-library/utility-functions.md#forward) aby upewnić się, że parametr funkcji ma żądanego typu.  
  
 Zgodność ze starszego kodu, klasa definiuje również funkcji identity `operator()` zwraca jej argument `left`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<narzędzie >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<narzędzie >](../standard-library/utility.md)



