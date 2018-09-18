---
title: pobiera _getws — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _getws
- gets
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _getts
- gets
- _getws
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 354678a99ec4c0abf172ff182f6f3f8b439448ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017499"
---
# <a name="gets-getws"></a>gets, _getws

Pobiera wiersz ze `stdin` strumienia. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [gets_s —, _getws_s —](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT. Bezpieczne wersje tych funkcji, gets_s — i _getws_s —, są nadal dostępne. Informacje na temat tych funkcji alternatywnych, zobacz [gets_s —, _getws_s —](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*buffer*<br/>
Lokalizacja magazynowa ciągu wejściowego.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość argumentu, jeśli to się powiedzie. A **NULL** wskaźnik wskazuje warunek błędu lub końca pliku. Użyj [ferror](../c-runtime-library/reference/ferror.md) lub [feof](../c-runtime-library/reference/feof.md) do określenia, które z nich ma wystąpić. Jeśli `buffer` jest **NULL**, te wywołają procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustawiają mechanizm errno jako `EINVAL`.

## <a name="remarks"></a>Uwagi

`gets` Funkcja odczytuje wiersz ze standardowego strumienia wejściowego `stdin` i zapisuje go w `buffer`. Linia składa się z wszystkich znaków, w tym pierwszego znaku nowego wiersza (\n). `gets` następnie zastępuje znak nowego wiersza znakiem null (\0) przed zwróceniem linii. Z kolei `fgets` funkcji zachowuje znak nowego wiersza. `_getws` jest wersją znaków dwubajtowych `gets`; jej argument i wartość zwracana to ciągi znaków dwubajtowych.

> [!IMPORTANT]
>  Ponieważ nie istnieje żaden sposób, aby ograniczyć liczbę znaków czytanych przez pobiera, niezaufane dane wejściowe mogą łatwo spowodować przeładowanie buforu. Zamiast nich należy używać słów kluczowych `fgets`.

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```
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

Należy pamiętać, że dane wejściowe dłuższe niż 20 znaków zostanie przepełnią bufor wierszy i prawie na pewno, że program ulega awarii.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Zobacz też

[Stream operacji We/Wy](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)