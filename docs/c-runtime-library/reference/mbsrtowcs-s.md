---
title: mbsrtowcs_s
ms.date: 11/04/2016
apiname:
- mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: a935b5181078f3b08ba5f2f89c581ed8cce8ded5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588831"
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

Konwertowanie ciągu znaków wielobajtowych przy bieżących ustawieniach regionalnych na jego reprezentację ciągu znaków dwubajtowych. Wersja [mbsrtowcs —](mbsrtowcs.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Liczba znaków, konwersji.

*wcstr*<br/>
Adres bufor do przechowywania wynikowy przekonwertować ciąg znaku dwubajtowego.

*sizeInWords*<br/>
Rozmiar *wcstr* w słowach (znaki dwubajtowe).

*mbstr*<br/>
Pośredni wskaźnik do lokalizacji ciąg znaków wielobajtowych do konwersji.

*Liczba*<br/>
Maksymalna liczba znaków dwubajtowych do przechowywania w *wcstr* buforu, nie wliczając końcowej wartości null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Wskaźnik do **mbstate_t** konwersji stan obiektu. Jeśli ta wartość jest wskaźnikiem typu null, jest używany obiekt stanu konwersji statycznej wewnętrznego. Ponieważ wewnętrzny **mbstate_t** obiekt nie jest metodą o bezpiecznych wątkach, zaleca się, że należy zawsze przekazuj parametr własne *mbstate* parametru.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli konwersja zakończy się pomyślnie, lub kod błędu.

|Warunek błędu|Zwraca wartość i **errno**|
|---------------------|------------------------------|
|*wcstr* jest pustym wskaźnikiem i *sizeInWords* > 0|**EINVAL**|
|*mbstr* jest wskaźnikiem wartości null|**EINVAL**|
|Ciąg pośrednio wskazywany przez *mbstr* zawiera wielobajtowy sekwencję, która nie jest prawidłowa dla bieżących ustawień regionalnych.|**EILSEQ**|
|Bufora docelowego jest zbyt mała, aby zawierać ciąg przekonwertowany (chyba że *liczba* jest **_TRUNCATE**; Aby uzyskać więcej informacji, zobacz Uwagi)|**ERANGE**|

Jeśli występuje jeden z tych warunków, wyjątek nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

**Mbsrtowcs_s —** funkcji konwertuje ciąg znaków wielobajtowych pośrednio wskazywany przez *mbstr* do znaków szerokich przechowywanych w bufor wskazywany przez *wcstr*, za pomocą stan konwersji, zawarte w *mbstate*. Konwersja będą nadal dla każdego znaku, dopóki nie jest spełniony jeden z następujących warunków:

- Wielobajtowy znak null zostanie osiągnięty.

- Napotkano nieprawidłowy znak wielobajtowy

- Liczba znaków szerokich przechowywanych w *wcstr* buforu equals *liczba*.

Ciąg docelowy *wcstr* zawsze jest zakończony znakiem null, nawet w przypadku błędu, chyba że *wcstr* jest wskaźnikiem wartości null.

Jeśli *liczba* jest specjalna wartość [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s —** konwertuje tyle ciągu jako będą dopasowania do buforu docelowego pozostawiając nadal miejsca na wartość null Element przerywający.

Jeśli **mbsrtowcs_s —** pomyślnie konwertuje ciąg źródłowy umieszcza rozmiar w znaki dwubajtowe przekonwertowanego ciągu i terminator o wartości null do  *&#42;pReturnValue*, podana  *pReturnValue* nie jest wskaźnikiem typu null. Dzieje się tak nawet wtedy, gdy *wcstr* argument jest wskaźnikiem typu null i umożliwia określenie wymagany rozmiar buforu. Należy pamiętać, że jeśli *wcstr* jest pustym wskaźnikiem, *liczba* jest ignorowana.

Jeśli *wcstr* nie jest wskaźnikiem typu null, obiekt wskaźnika wskazywany przez *mbstr* przypisano wskaźnikiem typu null, jeśli konwersja została zatrzymana, ponieważ osiągnięto kończącego znaku null. W przeciwnym razie jest przypisany adres przeszłości tylko ostatni znak wielobajtowy jest konwertowany, jeśli istnieje. Dzięki temu wywołania funkcji późniejszego ponownego uruchomienia konwersji, w którym to wywołanie jest zatrzymana.

Jeśli *mbstate* jest pustym wskaźnikiem, wewnętrznej biblioteki **mbstate_t** obiektu statycznego stan konwersji jest używany. Ponieważ tego wewnętrznego obiektu statycznego nie jest metodą o bezpiecznych wątkach, firma Microsoft zaleca, aby były przekazywane własne *mbstate* wartości.

Jeśli **mbsrtowcs_s —** napotka znaku wielobajtowego, który nie jest prawidłowa w bieżących ustawień regionalnych, umieszcza -1 w  *&#42;pReturnValue*, ustawia bufor docelowy *wcstr* pusty ciąg, ustawia **errno** do **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencji wskazywany przez *mbstr* i *wcstr* zachodziły na siebie, zachowanie **mbsrtowcs_s —** jest niezdefiniowana. **mbsrtowcs_s —** jest zależna od kategorii LC_TYPE bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie zachodziły na siebie oraz że *liczba* poprawnie odzwierciedla liczbę znaków wielobajtowych do przekonwertowania.

**Mbsrtowcs_s —** funkcja różni się od [mbstowcs_s —, _mbstowcs_s_l —](mbstowcs-s-mbstowcs-s-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane. Na przykład, aplikacja powinna używać **mbsrlen** zamiast **mbslen —**, jeśli kolejne wywołanie **mbsrtowcs_s —** jest używana zamiast **mbstowcs_s —**.

W języku C++ za pomocą tej funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) oraz te mogą automatycznie zastąpić starsze, niezabezpieczone funkcje przy użyciu ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Mbsrtowcs_s —** — funkcja jest bezpieczna wielowątkowych, jeśli żadna funkcja w bieżący wątek wywoła **setlocale** tak długo, jak ta funkcja jest wykonywany i *mbstate* argument jest Pusty wskaźnik.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbsrtowcs_s**|\<WChar.h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
