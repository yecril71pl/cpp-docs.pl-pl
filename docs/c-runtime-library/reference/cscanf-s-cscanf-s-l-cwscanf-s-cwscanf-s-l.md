---
title: _cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l
ms.date: 11/04/2016
apiname:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
ms.openlocfilehash: b49c464c7262a60bb7744a68c0144234e152edd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463703"
---
# <a name="cscanfs-cscanfsl-cwscanfs-cwscanfsl"></a>_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l

Odczyty sformatowanych danych z konsoli. Te bardziej bezpieczne wersje [_cscanf, _cscanf_l —, _cwscanf —, _cwscanf_l —](cscanf-cscanf-l-cwscanf-cwscanf-l.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _cscanf_s(
   const char *format [,
   argument] ...
);
int _cscanf_s_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf_s(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*Format*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Parametry opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Liczbę pól pomyślnie przekonwertowanych i przypisanych. Zwracana wartość nie uwzględnia pól, które zostały odczytane, ale nie przypisane. Wartość zwracana jest **EOF** dla próba odczytu na końcu pliku. Taka sytuacja może wystąpić, gdy dane wejściowe z klawiatury są przekierowywane na poziomie wiersza polecenia systemu operacyjnego. Zwracana wartość wynosząca 0 oznacza, że nie przydzielono żadnych pól.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *format* jest pustym wskaźnikiem, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EOF** i **errno** ustawiono **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Cscanf_s —** funkcja odczytuje dane bezpośrednio z konsoli w miejscach podanych przez *argument*. [_Getche](getch-getwch.md) funkcja jest używana do odczytu znaków. Każdy parametr opcjonalny musi być wskaźnikiem do zmiennej typu odpowiadającego specyfikatorowi typu w parametrze *format*. Format kontroluje interpretację danych wejściowych pola i ma taką samą formę i funkcjonuje jako *format* parametr [scanf_s](scanf-scanf-l-wscanf-wscanf-l.md) funkcji. Gdy **_cscanf_s —** zwykle funkcją wprowadzanych znaków nie są tak Jeśli ostatnie wywołanie było do **_ungetch**.

Podobnie jak inne bezpieczne wersje funkcji w **scanf** rodziny **_cscanf_s —** i **_cswscanf_s** wymagają argumentów rozmiaru dla znaków pola typu **c** , **C**, **s**, **S**, i **[**. Aby uzyskać więcej informacji, zobacz [scanf — specyfikacje szerokości](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Parametr rozmiaru ma typ **niepodpisane**, a nie **size_t**.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf_s —**|**_cscanf_s**|**_cscanf_s**|**_cwscanf_s**|
|**_tcscanf_s_l —**|**_cscanf_s_l**|**_cscanf_s_l**|**_cwscanf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cscanf_s —**, **_cscanf_s_l —**|\<conio.h>|
|**_cwscanf_s —**, **_cwscanf_s_l —**|\<conio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_cscanf_s.c
// compile with: /c
/* This program prompts for a string
* and uses _cscanf_s to read in the response.
* Then _cscanf_s returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int result, n[3];
   int i;

   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );
   _cprintf_s( "\r\nYou entered " );
   for( i=0; i<result; i++ )
      _cprintf_s( "%i ", n[i] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
You entered 1 2 3
```

## <a name="see-also"></a>Zobacz także

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
