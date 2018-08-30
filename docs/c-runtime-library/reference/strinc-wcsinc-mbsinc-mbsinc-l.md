---
title: _strinc, _wcsinc, _mbsinc, _mbsinc_l | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsinc
- _wcsinc
- _mbsinc_l
- _strinc
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsinc_l
- _strinc
- strinc
- _mbsinc
- _wcsinc
- wcsinc
- mbsinc
- _mbsinc_l
dev_langs:
- C++
helpviewer_keywords:
- _mbsinc function
- wcsinc function
- mbsinc_l function
- _strinc function
- strinc function
- _mbsinc_l function
- mbsinc function
- _wcsinc function
- _tcsinc function
- tcsinc function
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d714499ebb33d1d4dc2636ab80b2ad727ccac39
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195161"
---
# <a name="strinc-wcsinc-mbsinc-mbsincl"></a>_strinc, _wcsinc, _mbsinc, _mbsinc_l

Przesuwa wskaźnik ciągu o jeden znak.

> [!IMPORTANT]
> **_mbsinc** i **_mbsinc_l** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *_strinc(
   const char *current,
   _locale_t locale
);
wchar_t *_wcsinc(
   const wchar_t *current,
   _locale_t locale
);
unsigned char *_mbsinc(
   const unsigned char *current
);
unsigned char *_mbsinc_l(
   const unsigned char *current,
   _locale_t locale
);

```

### <a name="parameters"></a>Parametry

*bieżący*<br/>
Wskaźnik znaków.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wskaźnik do znaku, który poprzedza *bieżącego*.

## <a name="remarks"></a>Uwagi

**_Mbsinc** funkcja zwraca wskaźnik do pierwszego bajtu znaków wielobajtowego, który poprzedza *bieżącego*. **_mbsinc** rozpoznaje sekwencje znaków wielobajtowych według [wielobajtowa strona kodowa](../../c-runtime-library/code-pages.md) , jest obecnie w użyciu; **_mbsinc_l** jest identyczna, z tą różnicą, że zamiast tego używa przekazanego parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Funkcja generic tekst **_tcsinc**, zdefiniowana w Tchar.h, mapy i **_mbsinc** Jeśli **_MBCS** została zdefiniowana, lub **_wcsinc** Jeśli **_UNICODE** został zdefiniowany. W przeciwnym razie **_tcsinc** mapuje **_strinc**. **_strinc** i **_wcsinc** są wersjami pojedynczych bajtów znaków i znaków dwubajtowych **_mbsinc**. **_strinc** i **_wcsinc** są dostarczane tylko dla tego mapowania i nie powinny być używane w inny sposób. Aby uzyskać więcej informacji, zobacz [przy użyciu mapowania typ ogólny-tekst](../../c-runtime-library/using-generic-text-mappings.md) i [mapowania typ ogólny-tekst](../../c-runtime-library/generic-text-mappings.md).

Jeśli *bieżącego* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **EINVAL** i ustawia **errno** do **EINVAL**.

> [!IMPORTANT]
> Funkcje te mogą być podatne na zagrożenia przepełnienia buforu. Przepełnienia buforu może służyć do ataków systemu, ponieważ mogą one spowodować nieuzasadnione podniesienie poziomu uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsinc**|\<mbstring.h>|
|**_mbsinc_l**|\<mbstring.h>|
|**_strinc**|\<tchar.h >|
|**_wcsinc**|\<tchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
