---
title: tmpnam_s —, _wtmpnam_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8c6298c7b66c8967a4e5e23a37c3614edcddf3d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415531"
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s

Generowania nazw, który służy do tworzenia plików tymczasowych. Są to wersje [tmpnam — i _wtmpnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Wskaźnik, w którym będą przechowywane wygenerowana nazwa.

*sizeInChars*<br/>
Rozmiar buforu w znakach.

## <a name="return-value"></a>Wartość zwracana

W przypadku niepowodzenia obu tych funkcji zwraca 0 w przypadku powodzenia lub numer błędu.

### <a name="error-conditions"></a>Warunki błędów

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**Wartość zwracana**|**Zawartość***str* |
|**NULL**|wszystkie|**EINVAL —**|Nie zmodyfikowano|
|Nie **NULL** (wskazuje prawidłowy pamięci)|zbyt krótki|**ERANGE —**|Nie zmodyfikowano|

Jeśli *str* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwracać **einval —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zwraca nazwę pliku, który obecnie nie istnieje. **tmpnam_s —** zwraca nazwę unikatową w bieżącym katalogu roboczym. Należy zauważyć, że jeśli nazwa pliku jest pre oczekującego ukośnika odwrotnego i nie informacji ścieżki, takich jak \fname21, oznacza to, że nazwa jest nieprawidłowa dla bieżącego katalogu roboczego.

Aby uzyskać **tmpnam_s —**, można przechowywać tej nazwy pliku wygenerowanego w *str*. Maksymalna długość ciągu zwróconego przez **tmpnam_s —** jest **l_tmpnam_s —** zdefiniowanej w stdio —. H. Jeśli *str* jest **NULL**, następnie **tmpnam_s —** pozostawia wynik w statycznej buforu wewnętrznego. W związku z tym kolejnych wywołań zniszczyć tej wartości. Nazwa wygenerowana przez **tmpnam_s —** składa się nazwy pliku generowanych przez program i po pierwszym wywołaniu **tmpnam_s —**, rozszerzenie pliku numerów sekwencyjnych w podstawowej 32 (.1 .1vvvvvu, gdy **TMP _MAX_S** w stdio —. H jest **int_max —**).

**tmpnam_s —** dojść do ciągu znaków wielobajtowych argumenty zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowej OEM uzyskane automatycznie z systemu operacyjnego. **_wtmpnam_s —** jest wersja znaków dwubajtowych **tmpnam_s —**; argumentów i wartości **_wtmpnam_s —** są ciągami znaków dwubajtowych. **_wtmpnam_s —** i **tmpnam_s —** zachowują się tak samo, z wyjątkiem **_wtmpnam_s —** nie obsługuje ciągów znaków wielobajtowych.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
