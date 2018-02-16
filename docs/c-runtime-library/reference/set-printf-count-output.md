---
title: _set_printf_count_output | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_printf_count_output
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
- set_printf_count_output
- _set_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 279b14f0387348d322bbe09428af24daa5fd2f69
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output
Włącza lub wyłącza obsługę `%n` formatowania w [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)— funkcje rodziny.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _set_printf_count_output(  
   int enable  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enable`  
 Wartość inną niż zero, aby włączyć `%n` obsługuje, 0, aby wyłączyć `%n` obsługuje.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Stan `%n` obsługuje przed wywołaniem tej funkcji: Jeśli niezerowy `%n` włączona była obsługa, 0, jeśli zostało wyłączone.  
  
## <a name="remarks"></a>Uwagi  
 Ze względu na bezpieczeństwo, obsługę `%n` specyfikator formatu jest domyślnie wyłączona w `printf` i jej wariantów. Jeśli `%n` napotkano w `printf` jest specyfikacją formatu, domyślne zachowanie można wywołać program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Wywoływanie `_set_printf_count_output` z argumentem inną niż zero spowoduje, że `printf`-rodziny funkcji interpretować `%n` zgodnie z opisem w [składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_set_printf_count_output`|\<stdio.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_set_printf_count_output.c  
#include <stdio.h>  
  
int main()  
{  
   int e;  
   int i;  
   e = _set_printf_count_output( 1 );  
   printf( "%%n support was %sabled.\n",  
        e ? "en" : "dis" );  
   printf( "%%n support is now %sabled.\n",  
        _get_printf_count_output() ? "en" : "dis" );  
   printf( "12345%n6789\n", &i ); // %n format should set i to 5  
   printf( "i = %d\n", i );  
}  
```  
  
```Output  
%n support was disabled.  
%n support is now enabled.  
123456789  
i = 5  
```  
  
## <a name="see-also"></a>Zobacz też  
 [_get_printf_count_output](../../c-runtime-library/reference/get-printf-count-output.md)