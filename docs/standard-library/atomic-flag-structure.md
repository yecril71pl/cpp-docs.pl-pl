---
title: "atomic_flag — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs: C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d45d1cd6b0b0e4d12ee9a5567ee172cb7e772c3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atomicflag-structure"></a>atomic_flag — Struktura
Opisuje obiekt, który automatycznie ustawia i usuwa `bool` flagi. Operacje na atomic flagi są zawsze zwolnić blokady.  
  
## <a name="syntax"></a>Składnia  
  
```
struct atomic_flag;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Wyczyść](#clear)|Ustawia flagę przechowywanych `false`.|  
|[test_and_set](#test_and_set)|Ustawia flagę przechowywane `true` i zwraca wartość flagi początkowej.|  
  
## <a name="remarks"></a>Uwagi  
 `atomic_flag`obiekty mogą być przekazywane do funkcji nieczłonkowskich [atomic_flag_clear —](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit —](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set —](../standard-library/atomic-functions.md#atomic_flag_test_and_set), i [ atomic_flag_test_and_set_explicit —](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Mogą być inicjowane przy użyciu wartości `ATOMIC_FLAG_INIT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<atomic >  
  
 **Namespace:** Standard  
  
##  <a name="clear"></a>atomic_flag::Clear
 Ustawia `bool` Flaga, która jest przechowywana w `*this` do `false`, w ramach określonego [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.  
  
```
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Order`  
 A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="test_and_set"></a>atomic_flag::test_and_set
 Ustawia `bool` Flaga, która jest przechowywana w `*this` do `true`, w ramach określonego [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.  
  
```
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Order`  
 A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość początkowa flagi, które są przechowywane w `*this`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<niepodzielne >](../standard-library/atomic.md)



