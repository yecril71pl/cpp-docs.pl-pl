---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 8811bd0b6e4009cd6aba570e65d0687fab465614
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231367"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Odczytuje sformatowane dane ze standardowego strumienia wejściowego. Te wersje [scanf, _scanf_l, wscanf _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parametry

*Formatowanie*<br/>
Format ciąg kontrolny.

*argument*<br/>
Argumenty opcjonalne.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pól, które zostały pomyślnie przekonwertowane i przypisane. Wartość zwracana nie zawiera pól, które zostały odczytane, ale nie zostały przypisane. Wartość zwracana 0 wskazuje, że nie zostały przypisane żadne pola. Wartość zwracana to **eof** dla błędu lub jeśli znak końca pliku lub znak końca ciągu zostanie znaleziony w pierwszej próbie odczytania znaku. Jeśli *Format* jest **pustym** wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **scanf_s** i **wscanf_s** zwracać **EOF** i ustawić **errno** na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **scanf_s** odczytuje dane ze standardowego strumienia wejściowego, **stdin**i zapisuje je w *argumencie*. Każdy *argument* musi być wskaźnikiem do typu zmiennej, który odpowiada specyfikatorowi typu w *formacie*. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**wscanf_s** to dwubajtowa wersja **scanf_s**; argument *formatu* **wscanf_s** jest ciągiem znaków dwubajtowych. **wscanf_s** i **scanf_s** zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **scanf_s** nie obsługuje obecnie danych wejściowych ze strumienia Unicode.

Wersje tych funkcji, które mają sufiks **_l** są identyczne, z tą różnicą, że korzystają z parametru *locale* zamiast bieżących ustawień regionalnych wątku.

W przeciwieństwie do **scanf** i **wscanf**, **scanf_s** i **wscanf_s** wymagają określenia rozmiarów buforów dla niektórych parametrów. Określ rozmiary dla wszystkich parametrów **c**, **c**, **s**, **s**lub String **[]** . Rozmiar buforu w znakach jest przesyłany jako dodatkowy parametr. Natychmiast następuje po wskaźniku do bufora lub zmiennej. Na przykład w przypadku odczytywania ciągu rozmiar buforu dla tego ciągu jest przesyłany w następujący sposób:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

Rozmiar buforu zawiera wartość null terminalu. Możesz użyć pola Specyfikacja szerokości, aby upewnić się, że token, który jest odczytywany, mieści się w buforze. Gdy token jest zbyt duży, aby go dopasować, nic nie jest zapisywane w buforze, chyba że istnieje Specyfikacja szerokości.

> [!NOTE]
> Parametr size ma typ, a **`unsigned`** nie **size_t**. Użyj statycznego rzutowania, aby przekonwertować wartość **size_t** na **`unsigned`** 64-bitowe konfiguracje kompilacji.

Parametr rozmiaru buforu opisuje maksymalną liczbę znaków, a nie bajtów. W tym przykładzie szerokość typu buforu nie jest zgodna z szerokością specyfikatora formatu.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

Specyfikator formatu **S** oznacza użycie szerokości znaków, która jest "przeciwieństwem" do domyślnej szerokości obsługiwanej przez funkcję. Szerokość znaku jest jednobajtowa, ale funkcja obsługuje znaki dwubajtowe. Ten przykład odczytuje ciąg o długości do dziewięciu znaków jednobajtowych i umieszcza je w buforze znaków dwubajtowych. Znaki są traktowane jako wartości jednobajtowe. pierwsze dwa znaki są przechowywane w `ws[0]` , drugie dwa są przechowywane w `ws[1]` i tak dalej.

Ten przykład odczytuje pojedynczy znak:

```C
char c;
scanf_s("%c", &c, 1);
```

Gdy odczytywane są wiele znaków dla ciągów niezakończonych znakiem null, liczby całkowite są używane zarówno dla specyfikacji szerokości, jak i rozmiaru buforu.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

Aby uzyskać więcej informacji, zobacz [Specyfikacja szerokości scanf](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Aby uzyskać więcej informacji, zobacz [Formatowanie pól specyfikacji: scanf i wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**scanf_s**, **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**, **_wscanf_s_l**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Strumień standardowy obsługuje parametry **stdin**, **stdout**i **stderr** przed użyciem ich w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

Ten program tworzy następujące dane wyjściowe, gdy nadane dane wejściowe:

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[Regionalne](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf —, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
