---
title: _matherr
ms.date: 04/05/2018
api_name:
- _matherr
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _matherr
- matherr
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: 340e3b8562e1f0f564810bc63cf6bd2e87ffdf63
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952758"
---
# <a name="_matherr"></a>_matherr

Obsługuje błędy matematyczne.

## <a name="syntax"></a>Składnia

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Parametry

*ale*<br/>
Wskaźnik do struktury zawierającej informacje o błędzie.

## <a name="return-value"></a>Wartość zwracana

**_matherr** zwraca 0, aby wskazać błąd, lub wartość różną od zera, aby wskazać powodzenie. Jeśli **_matherr** zwraca wartość 0, może zostać wyświetlony komunikat o błędzie, a **errno** jest ustawiona na odpowiednią wartość błędu. Jeśli **_matherr** zwraca wartość różną od zera, żaden komunikat o błędzie nie jest wyświetlany i **errno** pozostaje niezmieniony.

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_matherr** przetwarza błędy generowane przez funkcje zmiennoprzecinkowe biblioteki matematycznej. Te funkcje wywołują **_matherr** w przypadku wykrycia błędu.

W przypadku specjalnej obsługi błędów można podać inną definicję **_matherr**. W przypadku korzystania z dynamicznie połączonej wersji biblioteki wykonawczej C (CRT) można zastąpić domyślną procedurę **_matherr** w pliku wykonywalnym klienta za pomocą wersji zdefiniowanej przez użytkownika. Nie można jednak zastąpić domyślnej procedury **_matherr** w kliencie DLL biblioteki DLL CRT.

Gdy wystąpi błąd w procedurze matematycznej, **_matherr** jest wywoływana ze wskaźnikiem do struktury typu **_exception** (zdefiniowanego w \<Math. h >) jako argument. Struktura **_exception** zawiera następujące elementy.

```C
struct _exception
{
    int    type;   // exception type - see below
    char*  name;   // name of function where error occurred
    double arg1;   // first argument to function
    double arg2;   // second argument (if any) to function
    double retval; // value to be returned by function
};
```

Element członkowski **typu** określa typ błędu matematycznego. Jest to jedna z następujących wartości zdefiniowana w \<Math. h >:

|Macro|Znaczenie|
|-|-|
| **_DOMAIN** | Błąd domeny argumentu |
| **_SING** | Argument Singularity |
| **_OVERFLOW** | Błąd przepełnienia zakresu |
| **_PLOSS** | Częściowe utrata istotności |
| **_TLOSS** | Łączna utrata istotności |
| **_UNDERFLOW** | Wynik jest zbyt mały, aby można go było przedstawić. (Ten warunek nie jest obecnie obsługiwany). |

**Nazwa** elementu członkowskiego struktury jest wskaźnikiem do ciągu zakończonego znakiem null zawierającego nazwę funkcji, która spowodowała błąd. Elementy członkowskie struktury **arg1** i **arg2** określają wartości, które spowodowały błąd. Jeśli podano tylko jeden argument, jest on przechowywany w **arg1**.

Domyślna wartość zwracana dla danego błędu to **retval**. W przypadku zmiany wartości zwracanej należy określić, czy wystąpił błąd w rzeczywistości.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_matherr**|\<math.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

```Output
Special: using absolute value: log: _DOMAIN error
log( -2.0 ) = 6.931472e-01
Special: using absolute value: log10: _DOMAIN error
log10( -5.0 ) = 6.989700e-01
Normal: log( 0.0 ) = -inf
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
