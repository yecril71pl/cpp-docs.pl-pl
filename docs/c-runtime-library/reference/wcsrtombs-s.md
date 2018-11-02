---
title: wcsrtombs_s
ms.date: 11/04/2016
apiname:
- wcsrtombs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 9ece21737b1e0b4d157b241286638ac376843fc6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459062"
---
# <a name="wcsrtombss"></a>wcsrtombs_s

Konwertuj ciąg znaku dwubajtowego na jego reprezentację ciągu znaków wielobajtowych. Wersja [wcsrtombs —](wcsrtombs.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Liczba znaków, konwersji.

*mbstr*<br/>
Adres buforu dla wynikowych konwersji ciągu znaków wielobajtowych.

*sizeInBytes*<br/>
Rozmiar w bajtach *mbstr* buforu.

*wcstr*<br/>
Wskazuje ciąg znaków dwubajtowych do konwersji.

*Liczba*<br/>
Maksymalna liczba bajtów, które mają być przechowywane w *mbstr* buforu, lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Wskaźnik do **mbstate_t** konwersji stan obiektu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu.

|Warunek błędu|Zwraca wartość i **errno**|
|---------------------|------------------------------|
|*mbstr* jest **NULL** i *sizeInBytes* > 0|**EINVAL**|
|*wcstr* jest **o wartości NULL**|**EINVAL**|
|Bufora docelowego jest zbyt mała, aby zawierać ciąg przekonwertowany (chyba że *liczba* jest **_TRUNCATE**; zobacz uwagi poniżej)|**ERANGE**|

Jeśli występuje którykolwiek z tych warunków, wyjątek nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

**Wcsrtombs_s —** funkcji konwertuje ciąg znaków dwubajtowych, wskazywana przez *wcstr* na znaki wielobajtowe przechowywane w bufor wskazywany przez *mbstr*przy użyciu Stan konwersji zawarte w *mbstate*. Konwersja będą nadal dla każdego znaku, dopóki nie jest spełniony jeden z następujących warunków:

- Szeroki znak null zostanie osiągnięty.

- Napotkano znak dwubajtowy, który nie może zostać przekonwertowany

- Liczbę bajtów przechowywanych w *mbstr* buforu equals *liczba*.

Ciąg docelowy jest zawsze zakończony znakiem null (nawet w przypadku błędu).

Jeśli *liczba* jest specjalna wartość [_TRUNCATE](../../c-runtime-library/truncate.md), następnie **wcsrtombs_s —** konwertuje tyle ciągu jako będą dopasowania do buforu docelowego pozostawiając nadal miejsca na wartość null Element przerywający.

Jeśli **wcsrtombs_s —** pomyślnie konwertuje ciąg źródłowy umieszcza rozmiar w bajtach przekonwertowanego ciągu, łącznie z terminatorem null do  *&#42;pReturnValue* (pod warunkiem  *pReturnValue* nie **NULL**). Dzieje się tak nawet wtedy, gdy *mbstr* argument jest **NULL** i zapewnia możliwość określenia wymagany rozmiar buforu. Należy pamiętać, że jeśli *mbstr* jest **NULL**, *liczba* jest ignorowana.

Jeśli **wcsrtombs_s —** napotka znakiem dwubajtowym, nie można przekonwertować na znak wielobajtowy umieszcza -1 w  *\*pReturnValue*, ustawia bufor docelowy pusty ciąg, ustawia **errno** do **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencji wskazywany przez *wcstr* i *mbstr* zachodziły na siebie, zachowanie **wcsrtombs_s —** jest niezdefiniowana. **wcsrtombs_s —** jest zależna od kategorii LC_TYPE bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie zachodziły na siebie oraz że *liczba* poprawnie odzwierciedla liczbę znaków dwubajtowych do przekonwertowania.

**Wcsrtombs_s —** funkcja różni się od [wcstombs_s —, _wcstombs_s_l —](wcstombs-s-wcstombs-s-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane. Na przykład, aplikacja będzie używać **wcsrlen** zamiast **wcslen —**, jeśli kolejne wywołanie **wcsrtombs_s —** były używane zamiast **wcstombs_s —**.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Wcsrtombs_s —** funkcja jest bezpieczna wielowątkowych, tak długo, jak wywołania funkcji, nie w bieżącym wątku **setlocale** podczas wykonywania tej funkcji i *mbstate* ma wartość null.

## <a name="example"></a>Przykład

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

void main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcsrtombs_s**|\<WChar.h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
