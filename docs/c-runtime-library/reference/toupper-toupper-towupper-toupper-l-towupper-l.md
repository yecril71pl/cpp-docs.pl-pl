---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 4/2/2020
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
- _o__toupper
- _o__toupper_l
- _o__towupper_l
- _o_toupper
- _o_towupper
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
ms.openlocfilehash: 943b66bf03420dc707415fd5da0ddf8cc3107d85
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913868"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Konwertuj znak na wielkie litery.

## <a name="syntax"></a>Składnia

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*s*<br/>
Znak do przekonwertowania.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur konwertuje kopię *c*, jeśli to możliwe, i zwraca wynik.

Jeśli *c* jest znakiem dwubajtowym, dla którego **iswlower** jest różna od zera, a istnieje odpowiedni znak dwubajtowy, dla którego [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) jest różna od zera, **towupper** zwraca odpowiedni znak dwubajtowy; w przeciwnym razie **towupper** zwraca *c* bez zmian.

Brak wartości zwracanej zastrzeżonej do wskazania błędu.

Aby **ToUpper** dać oczekiwane wyniki, [__isascii](isascii-isascii-iswascii.md) i [IsLower](islower-iswlower-islower-l-iswlower-l.md) muszą zwracać wartość różną od zera.

## <a name="remarks"></a>Uwagi

Każda z tych procedur konwertuje daną małą literę na wielką literę, jeśli jest to możliwe i odpowiednie. Konwersja przypadku **towupper** jest specyficzna dla ustawień regionalnych. W przypadku zmiany tylko znaków istotnych dla bieżących ustawień regionalnych. Funkcje bez sufiksu **_l** używają obecnie ustawionych ustawień regionalnych. Wersje tych funkcji z sufiksem **_l** przyjmują ustawienia regionalne jako parametr i używają go zamiast obecnie ustawionych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Aby **ToUpper** dać oczekiwane wyniki, [__isascii](isascii-isascii-iswascii.md) i [IsUpper](isupper-isupper-l-iswupper-iswupper-l.md) muszą zwracać wartość różną od zera.

[Procedury konwersji danych](../../c-runtime-library/data-conversion.md)

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**ToUpper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** i **_towupper_l** nie są zależne od ustawień regionalnych i nie są przeznaczone do bezpośredniego wywoływania. Są one przeznaczone do użytku wewnętrznego przez **_totupper_l**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ToUpper**|\<CType. h>|
|**_toupper**|\<CType. h>|
|**towupper**|\<CType. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [funkcji](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Zobacz też

[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[do funkcji](../../c-runtime-library/to-functions.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
