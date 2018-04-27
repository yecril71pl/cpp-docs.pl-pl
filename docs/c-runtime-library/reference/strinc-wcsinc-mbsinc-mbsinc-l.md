---
title: _strinc, _wcsinc, _mbsinc, _mbsinc_l | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 956a0c03d9242d0d8c2912c516e9ba4ed9a06683
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="strinc-wcsinc-mbsinc-mbsincl"></a>_strinc, _wcsinc, _mbsinc, _mbsinc_l

Przesuwa wskaźnik ciągu o jeden znak.

> [!IMPORTANT]
> **_mbsinc** i **_mbsinc_l** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Bieżący*<br/>
Wskaźnik znaków.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każdy z tych procedur zwraca wskaźnik do znaku poniższą *bieżącego*.

## <a name="remarks"></a>Uwagi

**_Mbsinc** funkcja zwraca wskaźnik do pierwszego bajtu znaków wielobajtowych, poniższą *bieżącego*. **_mbsinc** rozpoznaje wielobajtowych sekwencji znaków zgodnie z [strony kodowe wielobajtowe](../../c-runtime-library/code-pages.md) który jest aktualnie w użyciu; **_mbsinc_l** jest identyczny z tą różnicą, że parametr ustawień regionalnych, który jest przekazywany w zamian używa. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Funkcja zwykłego tekstu **_tcsinc**, zdefiniowanych w pliku Tchar.h, mapy **_mbsinc** Jeśli **_MBCS** została zdefiniowana, lub do **_wcsinc** Jeśli **_Unicode —** została zdefiniowana. W przeciwnym razie **_tcsinc** mapuje **_strinc**. **_strinc** i **_wcsinc** pojedynczych bajtów znaków i znaków dwubajtowych wersji **_mbsinc**. **_strinc** i **_wcsinc** są dostępne tylko dla tego mapowania i nie powinna być używana w inny sposób. Aby uzyskać więcej informacji, zobacz [przy użyciu mapowania zwykłego tekstu](../../c-runtime-library/using-generic-text-mappings.md) i [mapowania zwykłego tekstu](../../c-runtime-library/generic-text-mappings.md).

Jeśli *bieżącego* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca **einval —** i ustawia **errno** do **einval —**.

> [!IMPORTANT]
> Funkcje te mogą być podatne na zagrożenia przepełnienie buforu. Przepełnienia buforów może służyć do ataków systemu, ponieważ mogą one powodować nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsinc**|\<mbstring.h>|
|**_mbsinc_l**|\<mbstring.h>|
|**_strinc**|\<tchar.h >|
|**_wcsinc**|\<tchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
