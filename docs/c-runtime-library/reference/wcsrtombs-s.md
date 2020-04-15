---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 71a2206df9d3afb64fcaf62848988cf116d9071f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328108"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

Konwertuj szeroki ciąg znaków na jego wielobajtową reprezentację ciągu znaków. Wersja [wcsrtombs](wcsrtombs.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*pZawąkaWartość*<br/>
Rozmiar w bajtach przekonwertowanego ciągu, w tym zerowy terminator.

*mbstr*<br/>
Adres buforu dla wynikowego przekonwertowanego wielobajtowego ciągu znaków.

*rozmiarWzdjęty*<br/>
Rozmiar w bajtach buforu *mbstr.*

*wcstr*<br/>
Wskazuje szeroki ciąg znaków do konwersji.

*Liczba*<br/>
Maksymalna liczba bajtów, które mają być przechowywane w buforze *mbstr* lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t.**

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, kod błędu w przypadku awarii.

|Błąd|Zwracana wartość i **errno**|
|---------------------|------------------------------|
|*mbstr* ma **wartość NULL** i *rozmiarWzdjęty* > 0|**Einval**|
|*wcstr* ma **wartość NULL**|**Einval**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *liczba* jest **_TRUNCATE**; patrz Uwagi poniżej)|**Układ ERANGE**|

Jeśli wystąpi którykolwiek z tych warunków, nieprawidłowy wyjątek parametru jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie jest dozwolone, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **wcsrtombs_s** konwertuje ciąg szerokich znaków wskazywalnych przez *wcstr* na znaki wielobajtowe przechowywane w buforze wskazyowanym przez *mbstr,* przy użyciu stanu konwersji zawartego w *mbstate*. Konwersja będzie kontynuowana dla każdego znaku, dopóki nie zostanie spełniony jeden z następujących warunków:

- Napotkany znak o szerokości null

- Napotkany szeroki znak, który nie może zostać przekonwertowany

- Liczba bajtów przechowywanych w buforze *mbstr* jest równa *liczbie*.

Ciąg docelowy jest zawsze zakończony zerem (nawet w przypadku błędu).

Jeśli *count* jest specjalną wartością [_TRUNCATE](../../c-runtime-library/truncate.md), następnie **wcsrtombs_s** konwertuje tyle ciągu, ile zmieści się w buforze docelowym, pozostawiając jednocześnie miejsce na zerowy terminator.

Jeśli **wcsrtombs_s** pomyślnie konwertuje ciąg źródłowy, umieszcza rozmiar w bajtach przekonwertowanego ciągu, w tym terminatora zerowego, na *&#42;pReturnValue* (pod warunkiem, że *wartość zwrotu* nie jest **null).** Dzieje się tak, nawet jeśli *mbstr* argument jest **NULL** i zapewnia sposób określenia rozmiaru buforu wymagane. Należy zauważyć, że jeśli *mbstr* ma **wartość NULL**, *liczba* jest ignorowana.

Jeśli **wcsrtombs_s** napotka szeroki znak, nie można go przekonwertować na znak wielobajtowy, umieszcza -1 w * \*pReturnValue*, ustawia bufor docelowy na pusty ciąg, ustawia **errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazane przez *wcstr* i *mbstr* nakładają się na siebie, zachowanie **wcsrtombs_s** jest niezdefiniowane. **wcsrtombs_s** ma wpływ LC_TYPE kategorii bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, a *liczba ta* poprawnie odzwierciedla liczbę szerokich znaków do konwersji.

Funkcja **wcsrtombs_s** różni się od [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) możliwością ponownego uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne. Na przykład aplikacja będzie używać **wcsrlen** zamiast **wcslen**, jeśli kolejne wywołanie **wcsrtombs_s** zostały użyte zamiast **wcstombs_s**.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **wcsrtombs_s** jest bezpieczna wielowątkowej czynności, o ile żadna funkcja w bieżącym wątku wywołuje **setlocale** podczas wykonywania tej funkcji, a *mbstate* ma wartość null.

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

int main()
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
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
