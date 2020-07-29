---
title: scanf, _scanf_l, wscanf, _wscanf_l
ms.date: 10/21/2019
api_name:
- _wscanf_l
- scanf
- _scanf_l
- wscanf
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
- _tscanf
- _scanf_l
- wscanf
- _wscanf_l
- scanf
- _tscanf_l
helpviewer_keywords:
- tscanf_l function
- _tscanf_l function
- reading data [C++], from input streams
- _tscanf function
- data [C++], reading from input stream
- scanf_l function
- scanf function
- wscanf function
- _scanf_l function
- tscanf function
- formatted data [C++], from input streams
- wscanf_l function
- _wscanf_l function
ms.assetid: 73eac607-117f-4be4-9ff0-4afd9cf3c848
ms.openlocfilehash: 62f97c901bc7e6dc34a2db6ad80193cc4aaa986a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231354"
---
# <a name="scanf-_scanf_l-wscanf-_wscanf_l"></a>scanf, _scanf_l, wscanf, _wscanf_l

Odczytuje sformatowane dane ze standardowego strumienia wejściowego. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [scanf_s, _scanf_s_l, wscanf_s _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

> [!NOTE]
> W programie Visual Studio 2015 `printf` i `scanf` Rodzina funkcji zostały zadeklarowane jako **`inline`** i przenoszone do `<stdio.h>` `<conio.h>` nagłówków i. W przypadku migrowania starszego kodu w połączeniu z tymi funkcjami może być widoczny *LNK2019* . Aby uzyskać więcej informacji, zobacz [Visual C++ historię zmian 2003-2015](../../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

## <a name="syntax"></a>Składnia

```C
int scanf(
   const char *format [,
   argument]...
);
int _scanf_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf(
   const wchar_t *format [,
   argument]...
);
int _wscanf_l(
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

Zwraca liczbę pól, które zostały pomyślnie przekonwertowane i przypisane; wartość zwracana nie zawiera pól, które zostały odczytane, ale nie przypisane. Wartość zwracana przez 0 wskazuje, że nie przypisano żadnych pól.

Jeśli *Format* jest **pustym** wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **eof** i ustawiają **errno** na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **scanf** odczytuje dane ze standardowego strumienia wejściowego **stdin** i zapisuje dane w lokalizacji podanej przez *argument*. Każdy *argument* musi być wskaźnikiem do zmiennej typu odpowiadającego specyfikatorowi typu w *formacie*. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

> [!IMPORTANT]
> Podczas odczytywania ciągu z **scanf**, zawsze określaj szerokość formatu **% s** (na przykład **"% 32S"** zamiast **"% s"**); w przeciwnym razie nieprawidłowo sformatowane dane wejściowe mogą łatwo spowodować przepełnienie buforu. Alternatywnie Rozważ użycie [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) lub [fgets](fgets-fgetws.md).

**wscanf** to dwubajtowa wersja **scanf**; argument *formatu* **wscanf** jest ciągiem znaków dwubajtowych. **wscanf** i **scanf** zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **scanf** obecnie nie obsługuje danych wejściowych ze strumienia Unicode.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem ustawień regionalnych zamiast bieżących ustawień regionalnych wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf**|**scanf**|**scanf**|**wscanf**|
|**_tscanf_l**|**_scanf_l**|**_scanf_l**|**_wscanf_l**|

Aby uzyskać więcej informacji, zobacz [Formatowanie pól specyfikacji — funkcje scanf i funkcje wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**scanf**, **_scanf_l**|\<stdio.h>|
|**wscanf**, **_wscanf_l**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_scanf.c
// compile with: /W3
// This program uses the scanf and wscanf functions
// to read formatted input.

#include <stdio.h>

int main( void )
{
   int   i, result;
   float fp;
   char  c, s[81];
   wchar_t wc, ws[81];
   result = scanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws ); // C4996
   // Note: scanf and wscanf are deprecated; consider using scanf_s and wscanf_s
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
   result = wscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws ); // C4996
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

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
