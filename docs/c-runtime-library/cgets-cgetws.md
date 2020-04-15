---
title: _cgets, _cgetws
ms.date: 4/2/2020
api_name:
- _cgetws
- _cgets
- _o__cgets
- _o__cgetws
api_location:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cgetws
- _cgetws
- _cgets
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
ms.openlocfilehash: afffb691ca8bf8d180cac11ac5f16a84d871b1b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334417"
---
# <a name="_cgets-_cgetws"></a>_cgets, _cgetws

Pobiera ciąg znaków z konsoli. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT. Bezpieczne wersje tych funkcji, _cgets_s i _cgetws_s, są nadal dostępne. Aby uzyskać informacje na temat tych alternatywnych funkcji, zobacz [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```
char *_cgets(
   char *buffer
);
wchar_t *_cgetws(
   wchar_t *buffer
);
template <size_t size>
char *_cgets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_cgetws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Parametry

*Buforu*<br/>
Lokalizacja przechowywania danych.

## <a name="return-value"></a>Wartość zwracana

`_cgets`i `_cgetws` przywróć wskaźnik do początku `buffer[2]`ciągu, w punkcie . Jeśli `buffer` ma **wartość NULL**, te funkcje wywołują nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru](../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, aby kontynuować, `EINVAL`zwracają **null** i ustawić `errno` na .

## <a name="remarks"></a>Uwagi

Te funkcje odczytywać ciąg znaków z konsoli i przechowywać ciąg `buffer`i jego długość w lokalizacji wskazanej przez . Parametr `buffer` musi być wskaźnikiem do tablicy znaków. Pierwszy element tablicy, `buffer[0]`musi zawierać maksymalną długość (w znakach) ciągu do odczytu. Tablica musi zawierać wystarczającą ilość elementów do przechowywania ciągu, kończący się znak null ('\0') i 2 dodatkowe bajty. Funkcja odczytuje znaki do momentu odczytu kombinacji wiersza powrotu karetki (CR-LF) lub określonej liczby znaków. Ciąg jest przechowywany `buffer[2]`począwszy od . Jeśli funkcja odczytuje CR-LF, przechowuje znak null ('\0'). Funkcja następnie przechowuje rzeczywistą długość ciągu w `buffer[1]`drugim elemencie tablicy, .

Ponieważ wszystkie klawisze edycji są aktywne, gdy `_cgets` lub `_cgetws` jest wywoływana w oknie konsoli, naciśnięcie klawisza F3 powoduje powtórzenie ostatniego wprowadzonego wpisu.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_cgets`|\<> conio.h|
|`_cgetws`|\<conio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```c
// crt_cgets.c
// compile with: /c /W3
// This program creates a buffer and initializes
// the first byte to the size of the buffer. Next, the
// program accepts an input string using _cgets and displays
// the size and text of that string.

#include <conio.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   char buffer[83] = { 80 };  // Maximum characters in 1st byte
   char *result;

   printf( "Input line of text, followed by carriage return:\n");

   // Input a line of text:
   result = _cgets( buffer ); // C4996
   // Note: _cgets is deprecated; consider using _cgets_s
   if (!result)
   {
      printf( "An error occurred reading from the console:"
              " error code %d\n", errno);
   }
   else
   {
      printf( "\nLine length = %d\nText = %s\n",
              buffer[1], result );
   }
}
```

```Output

      A line of input.Input line of text, followed by carriage return:
Line Length = 16
Text = A line of input.
```

## <a name="see-also"></a>Zobacz też

[Operacje We/Wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)
