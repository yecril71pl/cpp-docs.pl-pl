---
title: "nothrow_t — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: nothrow_t
dev_langs: C++
helpviewer_keywords: nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 46c58f637123d140372ba368afa7a26ba17b3f94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nothrowt-structure"></a>nothrow_t — Struktura
Struktury jest używany jako parametr funkcji operatora nowe wskazująca, że funkcja powinna zwrócić pustego wskaźnika, aby zgłosić błąd alokacji, zamiast zgłosić wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```
struct std::nothrow_t {};
```  
  
## <a name="remarks"></a>Uwagi  
 Struktura pomaga kompilator, aby wybrać prawidłową wersję konstruktora. [nothrow](../standard-library/new-functions.md#nothrow) jest synonimem dla obiektów typu `std::nothrow_t`.  
  
## <a name="example"></a>Przykład  
 Zobacz [nowy operator](../standard-library/new-operators.md#op_new) i [nowy operator &#91; &#93;](../standard-library/new-operators.md#op_new_arr) przykłady `std::nothrow_t` jest używany jako parametr funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<nowy >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



