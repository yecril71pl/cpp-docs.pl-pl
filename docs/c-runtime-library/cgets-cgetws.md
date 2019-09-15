---
title: _cgets, _cgetws
ms.date: 11/04/2016
api_name:
- _cgetws
- _cgets
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
ms.openlocfilehash: aa258eaba34feec8ea25d780ea6392f195e37508
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944688"
---
# <a name="_cgets-_cgetws"></a>_cgets, _cgetws

Pobiera ciąg znaków z konsoli. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT. Bezpieczne wersje tych funkcji, _cgets_s i _cgetws_s, są nadal dostępne. Aby uzyskać informacje na temat tych funkcji alternatywnych, zobacz [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
>  Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*buffer*<br/>
Lokalizacja magazynu dla danych.

## <a name="return-value"></a>Wartość zwracana

`_cgets`i `_cgetws` zwraca wskaźnik do początku ciągu, w `buffer[2]`. Jeśli `buffer` ma **wartość null**, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracają **wartości null** i ustawiają `errno` na `EINVAL`.

## <a name="remarks"></a>Uwagi

Te funkcje odczytują ciąg znaków z konsoli programu i przechowują ciąg i jego długość w lokalizacji wskazywanej przez `buffer`. `buffer` Parametr musi być wskaźnikiem do tablicy znaków. Pierwszy element tablicy `buffer[0]`,, musi zawierać maksymalną długość (w znakach) ciągu, który ma zostać odczytany. Tablica musi zawierać wystarczającą liczbę elementów do przechowania ciągu, kończący znak null (' \ 0 ') i 2 dodatkowe bajty. Funkcja odczytuje znaki do momentu, aż zostanie odczytana kombinacja powrotu karetki liniowej (CR-LF) lub podanej liczby znaków. Ciąg jest przechowywany od `buffer[2]`. Jeśli funkcja odczytuje CR-LF, przechowuje znak null (' \ 0 '). Funkcja przechowuje następnie rzeczywistą długość ciągu w drugim elemencie Array, `buffer[1]`.

Ponieważ wszystkie klawisze edycji są aktywne, `_cgets` gdy `_cgetws` lub jest wywoływana w oknie konsoli, naciśnięcie klawisza F3 powtarza ostatnio wprowadzony wpis.

W C++programie te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_cgets`|\<conio.h>|
|`_cgetws`|\<CONIO. h > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```
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

## <a name="see-also"></a>Zobacz także

[We/wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)
