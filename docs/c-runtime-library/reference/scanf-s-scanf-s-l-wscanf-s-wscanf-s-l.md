---
title: scanf_s —, _scanf_s_l —, wscanf_s —, _wscanf_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
dev_langs:
- C++
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
caps.latest.revision: 33
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96b40d891c4148a92a3d2f0060401cd84b371d73
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="scanfs-scanfsl-wscanfs-wscanfsl"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Odczyty sformatowanych danych z Standardowy strumień wejściowy. Te wersje programu [scanf, _scanf_l —, wscanf —, _wscanf_l —](scanf-scanf-l-wscanf-wscanf-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Format*<br/>
Ciąg formatu w kontroli.

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pól pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Wartość zwracana jest **EOF** wystąpił błąd, lub jeśli napotkano znak końca pliku lub znak zakończenia ciągu w pierwszej próby odczytu znak. Jeśli *format* jest **NULL** wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **scanf_s —** i **wscanf_s —** zwracać **EOF** i ustaw **errno** do **einval —**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Scanf_s —** funkcja odczytuje dane z Standardowy strumień wejściowy **stdin** i zapisuje dane do lokalizacji, która jest określany przez *argument*. Każdy *argument* musi być wskaźnikiem do zmiennej typu, który odpowiada specyfikatorowi typu w *format*. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**wscanf_s —** jest wersja znaków dwubajtowych **scanf_s —**; *format* argument **wscanf_s —** jest ciągiem znaków dwubajtowych. **wscanf_s —** i **scanf_s —** zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. **scanf_s —** nie obsługuje obecnie danych wejściowych z strumienia UNICODE.

Wersje tych funkcji, które mają **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych, który jest przekazywany w zamiast bieżącego ustawienia regionalne wątku.

W odróżnieniu od **scanf** i **wscanf —**, **scanf_s —** i **wscanf_s —** wymagają określenia wszystkich parametrów typu wejściowychrozmiarbuforu**c**, **C**, **s**, **S**, lub string zestawów kontroli, które są ujęte w **[]**. Rozmiar buforu w znakach jest przekazywany jako dodatkowy parametr natychmiast po wskaźnik do buforu lub zmiennej. Na przykład jeśli odczytujesz ciąg rozmiar buforu dla tego ciągu jest przekazywany w następujący sposób:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

Rozmiar buforu obejmuje zakończenia wartości null. Szerokość pola specyfikacji służy do zapewnienia, że token, który jest odczytywany w zmieści się w buforze. Jeśli żadne pole Specyfikacja szerokości jest używany, a token odczytu w jest zbyt duży, aby zmieścić się w buforze, nic nie są zapisywane w tym buforu.

> [!NOTE]
> Parametr rozmiaru jest typu **niepodpisane**, a nie **size_t**. Użyj rzutowania statycznego do konwertowania **size_t** do wartości **niepodpisane** konfiguracje kompilacji dla 64-bitowej.

W poniższym przykładzie pokazano, opisujący parametr rozmiaru buforu maksymalną liczbę znaków, a nie w bajtach. W wywołaniu **wscanf_s —**, szerokość znaku, który wskazuje typ buforu jest niezgodna z szerokość znaków, który jest wskazywany przez specyfikator formatu.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**S** specyfikator formatu oznacza użycie szerokości znaków, która jest "przeciwne" domyślnej szerokości, który jest obsługiwany przez funkcję. Szerokość znaku jest jednobajtowe, ale funkcja obsługuje znaki dwubajtowe. W tym przykładzie odczytuje w ciągu maksymalnie 9 znaków jednego bajtu całej i umieszcza je w buforze znak podwójnej szerokości bajtów. Znaki są traktowane jako wartości jednobajtowe. pierwsze dwa znaki są przechowywane w `ws[0]`, następne dwa są przechowywane w `ws[1]`i tak dalej.

W przypadku znaków pojedynczy znak może wyglądać następująco:

```C
char c;
scanf_s("%c", &c, 1);
```

Przeczytaniu wielu znaków dla ciągów zakończone inną niż null liczb całkowitych są używane jako specyfikacja szerokości i rozmiar buforu.

```C
char c[4];
scanf_s("%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Aby uzyskać więcej informacji, zobacz [scanf — specyfikacje szerokości](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s —**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l —**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**scanf_s —**, **_scanf_s_l —**|\<stdio.h>|
|**wscanf_s —**, **_wscanf_s_l —**|\<stdio.h > lub \<wchar.h >|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu **stdin**, **stdout**, i **stderr**, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

Ten program tworzy następujące dane wyjściowe w przypadku danych wejściowych to:

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

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
