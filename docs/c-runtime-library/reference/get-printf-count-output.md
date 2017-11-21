---
title: "_get_printf_count_output — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
dev_langs: C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4373fc075e46110cbcef411b283b8566bf74508c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output
Wskazuje, czy [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)-rodziny funkcji obsługi `%n` format.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _get_printf_count_output();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli niezerowa `%n` jest obsługiwana, 0 Jeśli `%n` nie jest obsługiwane.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `%n` jest nieobsługiwane (domyślna), napotkania `%n` w ciągu formatu któregokolwiek z `printf` funkcje wywoła program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli `%n` włączona jest obsługa (zobacz [_set_printf_count_output —](../../c-runtime-library/reference/set-printf-count-output.md)) następnie `%n` będzie działać zgodnie z opisem w temacie [składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_printf_count_output`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_set_printf_count_output —](../../c-runtime-library/reference/set-printf-count-output.md).  
  
## <a name="see-also"></a>Zobacz też  
[_set_printf_count_output —](../../c-runtime-library/reference/set-printf-count-output.md)  
