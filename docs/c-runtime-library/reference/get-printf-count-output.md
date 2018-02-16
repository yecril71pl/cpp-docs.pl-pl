---
title: _get_printf_count_output | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_printf_count_output
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
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05184838f9ac68e697cc7ff326c33c266f865875
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
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
|`_get_printf_count_output`|\<stdio.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_set_printf_count_output —](../../c-runtime-library/reference/set-printf-count-output.md).  
  
## <a name="see-also"></a>Zobacz też  
[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)  
