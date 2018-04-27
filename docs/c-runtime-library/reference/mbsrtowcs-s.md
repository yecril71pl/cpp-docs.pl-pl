---
title: mbsrtowcs_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc125521b7db7537ecbbf3fe3c42ec6b8b8e1ada
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

Konwertowanie ciągu znaków wielobajtowych w bieżących ustawień regionalnych reprezentacji ciągu znaków dwubajtowych. Wersja [mbsrtowcs —](mbsrtowcs.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Liczba znaków konwersji.

*wcstr*<br/>
Adres buforu do przechowywania powstałe w ten sposób konwersji ciągu znaków dwubajtowych.

*sizeInWords*<br/>
Rozmiar *wcstr* słownie (znaki dwubajtowe).

*mbstr*<br/>
Pośredni wskaźnik do lokalizacji ciąg znaków wielobajtowych do skonwertowania.

*Liczba*<br/>
Maksymalna liczba znaki dwubajtowe, które mają być przechowywane w *wcstr* buforu Trwa przerywanie działania wartość null, z wyłączeniem lub [_truncate —](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Wskaźnik do **mbstate_t** konwersji stanu obiektu. Jeśli ta wartość jest wskaźnika o wartości null, jest używany obiekt stanu statyczne wewnętrzne konwersji. Ponieważ wewnętrznej **mbstate_t** obiekt nie jest bezpieczne wątkowo, zaleca się, że należy zawsze przekazuj własne *mbstate* parametru.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli konwersja zakończy się pomyślnie, lub błąd o kodzie błędu.

|Warunek błędu|Wartość zwracana i **errno**|
|---------------------|------------------------------|
|*wcstr* wskaźnik null i *sizeInWords* > 0.|**EINVAL —**|
|*mbstr* jest wskaźnika o wartości null|**EINVAL —**|
|Ciąg pośrednio wskazywana przez *mbstr* zawiera sekwencję wielobajtowe, która jest nieprawidłowa dla bieżącego ustawienia regionalne.|**EILSEQ —**|
|Bufor docelowy jest zbyt mały, aby pomieścił skonwertowany ciąg (chyba że *liczba* jest **_truncate —**; Aby uzyskać więcej informacji, zobacz Uwagi)|**ERANGE —**|

Jeśli występuje jeden z tych warunków, nieprawidłowy parametr wyjątek jest wywoływany zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, funkcja zwraca błąd o kodzie i ustawia **errno** wymienione w tabeli.

## <a name="remarks"></a>Uwagi

**Mbsrtowcs_s —** funkcja konwertuje ciąg znaków wielobajtowych pośrednio wskazywana przez *mbstr* w znaki dwubajtowe są przechowywane w buforze wskazywana przez *wcstr*, przez za pomocą konwersji stanie zawartymi w *mbstate*. Konwersja będzie kontynuowane dla każdego znaku, dopóki spełniony jest jeden z następujących warunków:

- Napotkano znak null wielobajtowe

- Napotkano nieprawidłowy znaków wielobajtowych

- Liczba znaki dwubajtowe są przechowywane w *wcstr* buforu equals *liczba*.

Ciąg docelowego *wcstr* jest zawsze zerem, nawet w przypadku błędu, chyba że *wcstr* jest wskaźnika o wartości null.

Jeśli *liczba* jest specjalna wartość [_truncate —](../../c-runtime-library/truncate.md), **mbsrtowcs_s —** konwertuje tyle ciągu jako spowoduje mieści się w bufor docelowy, pozostawiając nadal miejsca na wartość null terminator.

Jeśli **mbsrtowcs_s —** pomyślnie konwertuje ciąg źródłowy umieszcza w znaki dwubajtowe skonwertowany ciąg i terminatorem null do rozmiaru  *&#42;pReturnValue*, podany  *pReturnValue* nie jest wskaźnika o wartości null. Dzieje się tak nawet wtedy, gdy *wcstr* argument jest pusty wskaźnik i umożliwia określenie wymagany rozmiar buforu. Należy pamiętać, że jeśli *wcstr* wskaźnika o wartości null, jest *liczba* jest ignorowana.

Jeśli *wcstr* wskaźnika o wartości null, nie jest obiekt wskaźnika wskazywana przez *mbstr* jest przypisany wskaźnika o wartości null, jeśli konwersja została zatrzymana, ponieważ osiągnięto znak końcowy null. W przeciwnym razie wartość przypisano adres przeszłości tylko ostatnich znaków wielobajtowych przekonwertowany, jeśli istnieje. Umożliwia wywołanie funkcji kolejne ponowne uruchomienie konwersji, gdzie to wywołanie jest zatrzymana.

Jeśli *mbstate* jest pustego wskaźnika wewnętrznego biblioteki **mbstate_t** obiektu statycznego stan konwersji jest używany. Ten wewnętrzny obiekt statycznych nie jest bezpieczne wątkowo, dlatego zaleca się że przekazujesz własne *mbstate* wartości.

Jeśli **mbsrtowcs_s —** napotka znaków wielobajtowych, który nie jest prawidłowa w bieżących ustawień regionalnych, umieszcza -1 w  *&#42;pReturnValue*, ustawia bufor docelowy *wcstr* ciąg pusty, ustawia **errno** do **eilseq —**i zwraca **eilseq —**.

Jeśli sekwencje wskazywana przez *mbstr* i *wcstr* nakładają się zachowanie **mbsrtowcs_s —** jest niezdefiniowana. **mbsrtowcs_s —** dotyczy kategorii LC_TYPE bieżące ustawienia regionalne.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie pokrywają oraz że *liczba* poprawnie odzwierciedla liczbę znaków wielobajtowych do przekonwertowania.

**Mbsrtowcs_s —** funkcja różni się od [mbstowcs_s —, _mbstowcs_s_l —](mbstowcs-s-mbstowcs-s-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable. Na przykład, aplikacja, należy użyć **mbsrlen** zamiast **mbslen —**, jeśli kolejne wywołanie **mbsrtowcs_s —** jest używany zamiast **mbstowcs_s —**.

W języku C++ za pomocą tej funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (eliminując konieczność określić argument rozmiar) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje za pomocą ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Mbsrtowcs_s —** funkcji jest bezpieczne wielowątkowe, jeśli brak funkcji w bieżącym wywołania wątku **setlocale** tak długo, jak ta funkcja jest wykonywany i *mbstate* argument jest pustego wskaźnika.

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
