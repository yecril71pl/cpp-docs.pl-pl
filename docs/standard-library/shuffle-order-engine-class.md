---
title: "shuffle_order_engine — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- std::shuffle_order_engine [C++]
- std::shuffle_order_engine [C++], base
- std::shuffle_order_engine [C++], discard
- std::shuffle_order_engine [C++], base_type
- std::shuffle_order_engine [C++], seed
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5916ace0b29ae29beb05448e493e90d9f7df877
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine — Klasa
Generuje losowe sekwencji zmiana kolejności wartości zwracane z jego podstawowej aparatu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Engine`  
 Typ podstawowy aparatu.  
  
 `K`  
 **Tabela rozmiar**. Liczba elementów w buforze (tabeli). **Warunek wstępny**: `0 < K`  
  
## <a name="members"></a>Elementy członkowskie  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu opisuje *karty aparatu* daje wartości zmiana kolejności wartości zwracane przez silnik podstawowej. Każdy konstruktora wypełnienia tabeli wewnętrznej z `K` wartości zwracane przez aparat podstawowej, a element losowe wybrano z tabeli zleconą wartość.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<losowe >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<losowe >](../standard-library/random.md)

