---
title: _matherr
ms.date: 04/05/2018
apiname:
- _matherr
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
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: 980bf8a14ceace82a76562cc47d353f78dbca582
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445724"
---
# <a name="matherr"></a>_matherr

Obsługuje błędy matematyczne.

## <a name="syntax"></a>Składnia

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Parametry

*Z wyjątkiem*<br/>
Wskaźnik do struktury, zawierający informacje o błędzie.

## <a name="return-value"></a>Wartość zwracana

**_matherr** zwraca 0, aby wskazać błąd lub wartość różną od zera, informując o powodzeniu. Jeśli **_matherr** zwraca wartość 0, komunikat o błędzie mogą być wyświetlane i **errno** jest ustawiona na wartość odpowiedni komunikat o błędzie. Jeśli **_matherr** zwraca wartość różną od zera, bez komunikatu o błędzie jest wyświetlany i **errno** pozostaje bez zmian.

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Matherr** funkcja przetwarza błędów generowanych przez funkcje zmiennoprzecinkowe biblioteka funkcji matematycznych. Wywołania tych funkcji **_matherr** po wykryciu błędu.

Do obsługi błędów specjalne, możesz podać inną definicję **_matherr**. Jeśli używasz wersji połączone dynamicznie biblioteki wykonawczej języka C (CRT), można zastąpić domyślną **_matherr** rutynowej w kliencie pliku wykonywalnego przy użyciu wersji zdefiniowany przez użytkownika. Jednak nie można zastąpić domyślną **_matherr** rutynowej w kliencie biblioteki DLL biblioteki CRT.

Po wystąpieniu błędu w procedurze matematyczne **_matherr** jest wywoływana za pomocą wskaźnika do **_wyjątków** typ struktury (zdefiniowane w \<math.h >) jako argument. **_Wyjątków** struktura zawiera następujące elementy.

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

**Typu** elementu członkowskiego Określa typ błędu matematyczne. Jest to jeden z następujących wartości, zdefiniowane w \<math.h >:

|Macro|Znaczenie|
|-|-|
**_DOMENY**|Argument domeny błędów
**_SING**|Argument singularity
**_OVERFLOW**|Błąd w zakresie przepełnienia
**_PLOSS**|Częściowo utraciła istotności.
**_TLOSS**|Całkowita utrata znaczenia
**_UNDERFLOW**|Wynik jest za mały, aby mogły być reprezentowane. (Ten warunek nie jest obecnie obsługiwane.)

Element członkowski struktury **nazwa** jest wskaźnikiem do ciąg zakończony wartością null zawierający nazwę funkcji, które spowodowały błąd. Elementy członkowskie struktury **arg1** i **argument2** wpisz wartości, które spowodowały błąd. Jeśli tylko jeden argument zostanie podany, jest on przechowywany w **arg1**.

Domyślnie zwraca wartość danego błędu jest **retval**. Jeśli zmienisz wartość zwracaną, należy określić, czy rzeczywiście wystąpił błąd.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_matherr**|\<math.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
