---
title: "_get_terminate — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_terminate
- _get_terminate
- __get_terminate
dev_langs: C++
helpviewer_keywords:
- __get_terminate function
- get_terminate function
- _get_terminate function
ms.assetid: c8f168c4-0ad5-4832-a522-dd1ef383c208
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 87f0bc967175bd339d8e421d72de8a4f7d369631
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getterminate"></a>_get_terminate
Zwraca procedury zakończenia, który ma zostać wywołana przez `terminate`.  
  
## <a name="syntax"></a>Składnia  
  
```  
terminate_function _get_terminate( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do funkcji zarejestrowany przez [set_terminate —](../../c-runtime-library/reference/set-terminate-crt.md). Jeśli nie ustawiono żadnej funkcji, zwracana wartość może służyć do przywrócić domyślne zachowanie; Ta wartość może mieć wartości NULL.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_terminate`|\<EH.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [set_unexpected —](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [Zakończenie](../../c-runtime-library/reference/terminate-crt.md)   
 [Nieoczekiwany](../../c-runtime-library/reference/unexpected-crt.md)