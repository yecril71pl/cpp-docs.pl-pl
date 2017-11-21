---
title: "_get_unexpected — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_unexpected
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- __get_unexpected
- _get_unexpected
- get_unexpected
dev_langs: C++
helpviewer_keywords:
- __get_unexpected function
- get_unexpected function
- _get_unexpected function
ms.assetid: a5f7a7a0-18e0-485e-953d-db291068a1e8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 493dd3036e7f83ebf0e8fd94f62e57945ede52e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getunexpected"></a>_get_unexpected
Zwraca procedury zakończenia, który ma zostać wywołana przez `unexpected`.  
  
## <a name="syntax"></a>Składnia  
  
```  
unexpected_function _get_unexpected( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do funkcji zarejestrowany przez [set_unexpected —](../../c-runtime-library/reference/set-unexpected-crt.md). Jeśli nie ustawiono żadnej funkcji, zwracana wartość może służyć do przywrócić domyślne zachowanie; Ta wartość może mieć wartości NULL.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_unexpected`|\<EH.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [set_terminate —](../../c-runtime-library/reference/set-terminate-crt.md)   
 [Zakończenie](../../c-runtime-library/reference/terminate-crt.md)   
 [Nieoczekiwany](../../c-runtime-library/reference/unexpected-crt.md)