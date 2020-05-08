---
title: _strdec, _wcsdec, _mbsdec, _mbsdec_l
ms.date: 4/2/2020
api_name:
- _wcsdec
- _strdec
- _mbsdec
- _mbsdec_l
- _o__mbsdec
- _o__mbsdec_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strdec
- mbsdec_l
- strdec
- _mbsdec
- _mbsdec_l
- mbsdec
- wcsdec
- _wcsdec
helpviewer_keywords:
- mbsdec_l function
- mbsdec function
- tcsdec function
- _tcsdec function
- _strdec function
- _wcsdec function
- _mbsdec_l function
- strdec function
- wcsdec function
- _mbsdec function
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
ms.openlocfilehash: c3988beac1a3c1b3d7fa831405208ddc564456a3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914496"
---
# <a name="_strdec-_wcsdec-_mbsdec-_mbsdec_l"></a>_strdec, _wcsdec, _mbsdec, _mbsdec_l

Przenosi wskaźnik ciągu z powrotem o jeden znak.

> [!IMPORTANT]
> **mbsdec** i **mbsdec_l** nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned char *_strdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned wchar_t *_wcsdec(
   const unsigned wchar_t *start,
   const unsigned wchar_t *current
);
unsigned char *_mbsdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned char *_mbsdec_l(
   const unsigned char *start,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Start*<br/>
Wskaźnik na dowolny znak (lub dla **_mbsdec** i **_mbsdec_l**, pierwszy bajt dowolnego znaku wielobajtowego) w ciągu źródłowym; *początek* musi poprzedzać *bieżącą* wartość w ciągu źródłowym.

*bieżący*<br/>
Wskaźnik na dowolny znak (lub dla **_mbsdec** i **_mbsdec_l**, pierwszy bajt dowolnego znaku wielobajtowego) w ciągu źródłowym; *Bieżąca* wartość musi następować po *rozpoczęciu* w ciągu źródłowym.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsdec**, **_mbsdec_l**, **_strdec**i **_wcsdec** każdy zwraca wskaźnik do znaku, który bezpośrednio poprzedza *bieżące*; **_mbsdec** zwraca **wartość null** , jeśli wartość parametru *Start* jest większa lub równa wartości *Current*. **_tcsdec** mapuje do jednej z tych funkcji, a jej wartość zwracana zależy od mapowania.

## <a name="remarks"></a>Uwagi

Funkcje **_mbsdec** i **_mbsdec_l** zwracają wskaźnik do pierwszego bajtu znaku wielobajtowego, który bezpośrednio poprzedza *bieżącą* wartość w ciągu, który zawiera *początek*.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji [, zobacz setlocals, _wsetlocale](setlocale-wsetlocale.md) .  **_mbsdec** rozpoznaje sekwencje znaków wielobajtowych zgodnie z aktualnie używanymi ustawieniami regionalnymi, podczas gdy **_mbsdec_l** jest identyczny, z tą różnicą, że zamiast tego używa parametru ustawień regionalnych, który został przesłany. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli parametr *Start* lub *Current* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **EINVAL** i ustawia **errno** na **EINVAL**.

> [!IMPORTANT]
> Te funkcje mogą być narażone na zagrożenia przepełnienia buforu. Przepełnienia buforu mogą służyć do ataków systemu, ponieważ mogą one spowodować nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsdec**|**_strdec**|**_mbsdec**|**_wcsdec**|

**_strdec** i **_wcsdec** są wersjami jednobajtowymi znaków i **_mbsdec** i **_mbsdec_l**. **_strdec** i **_wcsdec** są dostępne tylko dla tego mapowania i nie powinny być używane w inny sposób.

Aby uzyskać więcej informacji, zobacz [Korzystanie z mapowań tekstu ogólnego](../../c-runtime-library/using-generic-text-mappings.md) i [mapowań tekstu ogólnego](../../c-runtime-library/generic-text-mappings.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_mbsdec**|\<mbstring. h>|\<Mbctype. h>|
|**_mbsdec_l**|\<mbstring. h>|\<Mbctype. h>|
|**_strdec**|\<Używanie TCHAR. h>||
|**_wcsdec**|\<Używanie TCHAR. h>||

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie **_tcsdec**.

```cpp
// crt_tcsdec.cpp
// Compile by using: cl /EHsc crt_tcsdec.cpp
#include <iostream>
#include <tchar.h>
using namespace std;

int main()
{
   const TCHAR *str = _T("12345");
   cout << "str: " << str << endl;

   const TCHAR *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   TCHAR *answer;
   answer = _tcsdec( str, str2 );
   cout << "answer: " << answer << endl;

   return (0);
}
```

W poniższym przykładzie pokazano użycie **_mbsdec**.

```cpp
// crt_mbsdec.cpp
// Compile by using: cl /EHsc crt_mbsdec.c
#include <iostream>
#include <mbstring.h>
using namespace std;

int main()
{
   char *str = "12345";
   cout << "str: " << str << endl;

   char *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   unsigned char *answer;
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));

   cout << "answer: " << answer << endl;

   return (0);
}
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
