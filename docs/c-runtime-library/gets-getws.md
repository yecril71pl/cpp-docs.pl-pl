---
title: gets, _getws
ms.date: 4/2/2020
api_name:
- _getws
- gets
- _o__getws
- _o_gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getts
- gets
- _getws
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
ms.openlocfilehash: a1fd3218f75079554d049d4ef4c3691a2fbdd542
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349317"
---
# <a name="gets-_getws"></a>gets, _getws

Pobiera wiersz ze `stdin` strumienia. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT. Bezpieczne wersje tych funkcji, gets_s i _getws_s, są nadal dostępne. Aby uzyskać informacje na temat tych alternatywnych funkcji, zobacz [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```
char *gets(
   char *buffer
);
wchar_t *_getws(
   wchar_t *buffer
);
template <size_t size>
char *gets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_getws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Parametry

*Buforu*<br/>
Lokalizacja przechowywania ciągu wejściowego.

## <a name="return-value"></a>Wartość zwracana

Zwraca jego argument, jeśli zakończy się pomyślnie. Wskaźnik **NULL** wskazuje błąd lub warunek końca pliku. Użyj [ferror](../c-runtime-library/reference/ferror.md) lub [feof,](../c-runtime-library/reference/feof.md) aby ustalić, który z nich wystąpił. Jeśli `buffer` ma **wartość NULL**, te funkcje wywołują nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru](../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje zwracają wartość `EINVAL` **NULL** i ustawiają errno na .

## <a name="remarks"></a>Uwagi

Funkcja `gets` odczytuje wiersz ze standardowego `stdin` strumienia `buffer`wejściowego i przechowuje go w pliku . Wiersz składa się ze wszystkich znaków do pierwszego znaku nowego wiersza włącznie ('\n'). `gets`następnie zastępuje znak nowego wiersza znakiem zerowym ("\0") przed zwróceniem wiersza. Z kolei `fgets` funkcja zachowuje znak nowego linii. `_getws`jest wersją o `gets`szerokim charakterze ; jego argument i zwracana wartość są ciągami znaków szerokich znaków.

> [!IMPORTANT]
> Ponieważ nie ma sposobu, aby ograniczyć liczbę znaków odczytywanych przez pobiera, niezaufanych danych wejściowych może łatwo spowodować przekroczenia buforu. Zamiast tego użyj polecenia cmdlet `fgets`.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```c
// crt_gets.c
// compile with: /WX /W3

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C4996
   // Danger: No way to limit input to 20 chars.
   // Consider using gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

Należy zauważyć, że wejście dłuższe niż 20 znaków spowoduje przekroczenie buforu wiersza i prawie na pewno spowoduje awarię programu.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
