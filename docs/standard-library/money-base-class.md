---
title: "money_base — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocmon/std::money_base
dev_langs: C++
helpviewer_keywords: money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b3243807c407fa4deeb30b8f35aa6f7acb13707
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="moneybase-class"></a>money_base — Klasa
Klasa opisuje, wyliczenia i struktury wspólne dla wszystkich specjalizacji szablonu klasy [moneypunct —](../standard-library/moneypunct-class.md).  
  
## <a name="syntax"></a>Składnia  
```    
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};  
```  
## <a name="remarks"></a>Uwagi  
 Wyliczenie **części** opisano możliwe wartości w elementach pola tablicy we wzorcu struktury. Wartości **części** są:  
  
- **Brak** odpowiada zero lub więcej spacji lub wygenerowanie nothing.  
  
- **znak** zgodny lub wygenerowanie znak dodatnią lub ujemną.  
  
- **miejsce** odpowiada zero lub więcej spacji lub wygenerowanie spacją.  
  
- **symbol** zgodny lub wygenerowanie symbol waluty.  
  
- **wartość** zgodny lub wygenerowanie wartość pieniężną.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



