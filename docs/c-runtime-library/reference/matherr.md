---
title: "_matherr — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _matherr
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
- _matherr
- matherr
dev_langs: C++
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d4a39224f643ada9f155e71d3a7cb48be8811398
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="matherr"></a>_matherr
Obsługuje błędy matematyczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *z wyjątkiem*  
 Wskaźnik do struktury zawierający informacje o błędzie.  
  
## <a name="return-value"></a>Wartość zwracana  
 _**matherr —** zwraca wartość 0, aby wskazać błąd lub wartość niezerową, informując o powodzeniu. Jeśli \_ **matherr —** zwraca wartość 0, komunikat o błędzie mogą być wyświetlane i `errno` ma ustawioną wartość odpowiednią błędu. Jeśli \_ **matherr —** zwraca wartość różną od zera, żaden komunikat o błędzie jest wyświetlany i `errno` pozostaje niezmieniona.  
  
 Aby uzyskać więcej informacji na temat kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 _**Matherr —** funkcja przetwarza błędy generowane przez funkcje liczb zmiennoprzecinkowych biblioteki matematyczne. Wywołanie funkcji \_ **matherr —** gdy zostaje wykryty błąd.  
  
 Do obsługi błędów specjalne, możesz podać innej definicji _**matherr —**. Jeśli używasz dynamicznie połączony wersja biblioteki wykonawczej języka C (Msvcr90.dll), można zastąpić domyślną \_ **matherr —** rutynowych w kliencie pliku wykonywalnego z wersją zdefiniowane przez użytkownika. Jednak nie można zastąpić domyślną `_matherr` rutynowych w kliencie biblioteki DLL z Msvcr90.dll.  
  
 Po wystąpieniu błędu w procedury matematyczne, _**matherr —** jest wywoływana za pomocą wskaźnika do **_exception —** wpisz strukturę (zdefiniowaną w Math.h) jako argumentu. **_Exception —** struktura zawiera następujące elementy.  
  
 **int — typ**  
 Typ wyjątku.  
  
 **CHAR \*nazwy**  
 Nazwa funkcji, w którym wystąpił błąd.  
  
 **Podwójne arg1**, **arg2**  
 Pierwszy i drugi (jeśli istnieją) argumenty funkcji.  
  
 **retval podwójne**  
 Wartość zwracana przez funkcję.  
  
 **Typu** Określa typ błędu matematycznych. Jest jednym z następujących wartości zdefiniowane w Math.h.  
  
 `_DOMAIN`  
 Argument domeny błędów.  
  
 `_SING`  
 Argument singularity.  
  
 `_OVERFLOW`  
 Zakres błąd przepełnienia.  
  
 `_PLOSS`  
 Częściowo utraciła istotności.  
  
 `_TLOSS`  
 Całkowita utrata istotności.  
  
 `_UNDERFLOW`  
 Wynik jest za mały, aby mogła być przedstawiana. (Ten warunek nie jest obecnie obsługiwana.)  
  
 Element członkowski struktury **nazwa** jest wskaźnikiem do zerem ciąg zawierający nazwę funkcji, który spowodował błąd. Elementy członkowskie struktury **arg1** i **arg2** określić wartości, które spowodowały błąd. (Jeśli tylko jeden argument zostanie określony, dane są przechowywane w **arg1**.)  
  
 Wartość domyślna zwracana wartość dla danego błędu to **retval**. Jeśli zmienisz wartość zwrotną, należy określić, czy rzeczywiście wystąpił błąd.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_matherr`|\<Math.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_matherr.c  
/* illustrates writing an error routine for math   
 * functions. The error function must be:  
 *      _matherr  
 */  
  
#include <math.h>  
#include <string.h>  
#include <stdio.h>  
  
int main()  
{  
    /* Do several math operations that cause errors. The _matherr  
     * routine handles _DOMAIN errors, but lets the system handle  
     * other errors normally.  
     */  
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );  
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );  
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );  
}  
  
/* Handle several math errors caused by passing a negative argument  
 * to log or log10 (_DOMAIN errors). When this happens, _matherr  
 * returns the natural or base-10 logarithm of the absolute value  
 * of the argument and suppresses the usual error message.  
 */  
int _matherr( struct _exception *except )  
{  
    /* Handle _DOMAIN errors for log or log10. */  
    if( except->type == _DOMAIN )  
    {  
        if( strcmp( except->name, "log" ) == 0 )  
        {  
            except->retval = log( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
        else if( strcmp( except->name, "log10" ) == 0 )  
        {  
            except->retval = log10( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
    }  
    printf( "Normal: " );  
    return 0;    /* Else use the default actions */  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   