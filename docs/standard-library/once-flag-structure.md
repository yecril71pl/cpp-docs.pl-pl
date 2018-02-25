---
title: "once_flag — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 482ef221338651ef3e6f6ec272c1a48984d40912
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="onceflag-structure"></a>once_flag — Struktura
Reprezentuje `struct` używany przy użyciu funkcji szablonu [call_once —](../standard-library/mutex-functions.md#call_once) aby upewnić się, że inicjowania kodu zostanie wywołana tylko raz, nawet w obecności wielu wątków wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
once_flag — struktura {constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag — & — operator =(const once_flag&);};  
  
## <a name="remarks"></a>Uwagi  
 `once_flag` `struct` Ma konstruktora domyślnego.  
  
 Obiekty typu `once_flag` mogą być tworzone, ale nie można skopiować.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<obiektu mutex >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



