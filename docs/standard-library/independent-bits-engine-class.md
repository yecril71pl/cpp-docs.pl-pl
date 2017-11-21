---
title: "independent_bits_engine — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: random/std::independent_bits_engine
dev_langs: C++
helpviewer_keywords: independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 09ee64a2e93d909533a0b2e4968a0fc48a951b08
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="independentbitsengine-class"></a>independent_bits_engine — Klasa
Generuje sekwencję losowych liczb z określoną liczbę bitów za pomocą liczby bitów przepakowania spośród wartości zwróconych przez silnik podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Engine, size_t W, class UIntType>  
class independent_bits_engine;  
```  
  
### <a name="parameters"></a>Parametry  
 `Engine`  
 Typ podstawowy aparatu.  
  
 `W`  
 **Word rozmiar**. Rozmiar w bitach każdą liczbę wygenerowany. **Warunek wstępny**:`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 Typ wyniku liczbę całkowitą bez znaku. Dla typów możliwych [ \<losowe >](../standard-library/random.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu opisuje *karty aparatu* daje wartości przez przepakowaniu bitów spośród wartości zwróconych przez silnik podstawowej, co powoduje `W`-bit wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<losowe >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<losowe >](../standard-library/random.md)

