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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1c60cf14334a0dcc0492b23da10a36c3219bb699
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919899"
---
# <a name="gets-_getws"></a>gets, _getws

Pobiera wiersz ze `stdin` strumienia. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT. Bezpieczne wersje tych funkcji, gets_s i _getws_s, są nadal dostępne. Aby uzyskać informacje na temat tych funkcji alternatywnych, zobacz [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*buforu*<br/>
Lokalizacja magazynu dla ciągu wejściowego.

## <a name="return-value"></a>Wartość zwracana

Zwraca swój argument, jeśli powodzenie. Wskaźnik o **wartości null** wskazuje błąd lub stan końca pliku. Użyjelement lub [feof](../c-runtime-library/reference/feof.md) [, aby](../c-runtime-library/reference/ferror.md) określić, który z nich wystąpił. Jeśli `buffer` ma **wartość null**, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **wartość null** i ustawiają errno `EINVAL`na.

## <a name="remarks"></a>Uwagi

`gets` Funkcja odczytuje wiersz ze standardowego strumienia `stdin` wejściowego i zapisuje go w `buffer`. Wiersz składa się ze wszystkich znaków do i łącznie z pierwszym znakiem nowego wiersza ("\n"). `gets`następnie zastępuje znak nowego wiersza znakiem null (' \ 0 ') przed zwróceniem wiersza. W przeciwieństwie `fgets` funkcja zachowuje znak nowego wiersza. `_getws`to wersja znaku dwubajtowego `gets`; jego argument i wartość zwracana są ciągami znaków dwubajtowych.

> [!IMPORTANT]
> Ponieważ nie ma możliwości ograniczenia liczby znaków odczytywanych przez pobranie, niezaufane dane wejściowe mogą łatwo spowodować przepełnienie buforu. Zamiast tego użyj polecenia cmdlet `fgets`.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../c-runtime-library/secure-template-overloads.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`gets`|\<stdio. h>|
|`_getws`|\<stdio. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

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

Należy pamiętać, że dane wejściowe dłuższe niż 20 znaków przekroczą bufor wiersza i prawie z tego powodu spowodują awarię programu.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
