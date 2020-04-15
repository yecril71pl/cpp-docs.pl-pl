---
title: _mbsnbcat, _mbsnbcat_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_l
- _mbsnbcat
- _o__mbsnbcat
- _o__mbsnbcat_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbcat
- mbsnbcat_l
- _mbsnbcat
- _mbsnbcat_l
helpviewer_keywords:
- tcsncat_l function
- _tcsncat function
- mbsnbcat_l function
- mbsnbcat function
- _mbsnbcat_l function
- _tcsncat_l function
- _mbsnbcat function
- tcsncat function
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
ms.openlocfilehash: 7598b20db4698ff8f95fbcefa00864be1b958447
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340802"
---
# <a name="_mbsnbcat-_mbsnbcat_l"></a>_mbsnbcat, _mbsnbcat_l

Dołącza co najwyżej pierwsze **n** bajtów jednego ciągu znaków wielobajtowych do drugiego. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned char *_mbsnbcat(
   unsigned char *dest,
   const unsigned char *src,
   size_t count
);
unsigned char *_mbsnbcat_l(
   unsigned char *dest,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char *_mbsnbcat(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsnbcat_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Dest*<br/>
Ciąg docelowy znaków z końców zerowych z wielobajtowym znakiem docelowym.

*src*<br/>
Ciąg źródłowy wielobajtowy znak zakończony z wartością null.

*Liczba*<br/>
Liczba bajtów od *src* do dołączyć do *dest*.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsnbcat** zwraca wskaźnik do ciągu docelowego. Żadna wartość zwracana nie jest zarezerwowana, aby wskazać błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_mbsnbcat** dołącza co najwyżej pierwsze bajty *zliczania* *src* do *dest*. Jeśli bajt bezpośrednio poprzedzający znak null w *dest* jest bajtem wiodącym, początkowy bajt *src* zastępuje ten bajt ołowiu. W przeciwnym razie początkowy bajt *src* zastępuje kończący się znak zerowy *dest*. Jeśli w *src* pojawi się bajt zerowy przed dołączeniem bajtów *zliczania,* **_mbsnbcat** dołącza wszystkie bajty od *src*, aż do znaku null. Jeśli *liczba* jest większa niż długość *src*, długość *src* jest używana zamiast *liczyć*. Wynikowy ciąg jest zakończony znakiem zerowym. Jeśli kopiowanie odbywa się między ciągami, które nakładają się na siebie, zachowanie jest niezdefiniowane.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. **Wersja _mbsnbcat** funkcji używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; _mbsnbcat_l **_mbsnbcat_l** wersja jest identyczna, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** Użyj ciągu zakończonego wartością null. Ciąg zakończony z wartością null nie może przekraczać rozmiaru buforu docelowego. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Jeśli *dest* lub *src* ma **wartość NULL**, funkcja wygeneruje nieprawidłowy błąd parametru, zgodnie z opisem w weryfikacji [parametrów](../../c-runtime-library/parameter-validation.md). Jeśli błąd jest obsługiwany, funkcja zwraca **wartość EINVAL** i ustawia **errno** na **EINVAL**.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_l**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcat**|\<mbstring.h>|
|**_mbsnbcat_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)<br/>
