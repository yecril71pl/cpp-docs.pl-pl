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
ms.openlocfilehash: de697e26d04e9d70cb1bbbdf4ecbf269d6918e4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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



