---
title: iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l
ms.date: 11/04/2016
apiname:
- iscntrl
- _iswcntrl_l
- _iscntrl_l
- iswcntrl
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istcntrl_l
- _iswcntrl_l
- iswcntrl
- _iscntrl_l
- iscntrl
- _istcntrl
helpviewer_keywords:
- iscntrl function
- _iscntrl_l function
- _iswcntrl_l function
- _istcntrl function
- istcntrl function
- iswcntrl function
- _istcntrl_l function
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
ms.openlocfilehash: 150073e78426f5029dd46cbc6766fbd6a2a242e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157425"
---
# <a name="iscntrl-iswcntrl-iscntrll-iswcntrll"></a>iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l

Określa, czy liczba całkowita reprezentuje znak kontrolny.

## <a name="syntax"></a>Składnia

```C
int iscntrl(
   int c
);
int iswcntrl(
   wint_t c
);
int _iscntrl_l(
   int c,
   _locale_t locale
);
int _iswcntrl_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Liczba całkowita to testowania

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli *c* jest szczególną reprezentacją znaku kontrolnego. **iscntrl** zwraca wartość różną od zera, jeśli *c* jest znakiem formantu (0x00-0x1F or 0x7F). **iswcntrl —** zwraca wartość różną od zera, jeśli *c* jest formantem szerokość znaków. Każda z tych procedur zwraca 0, jeśli *c* nie spełnia warunku testowego.

Wersje tych funkcji, które mają **_l** sufiksa używa przekazanego parametru ustawień regionalnych, zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Zachowanie **iscntrl** i **_iscntrl_l —** jest niezdefiniowane, jeżeli *c* nie jest równy EOF lub z zakresu od 0 do 0xFF włącznie. Jeśli jest używana biblioteka debugowania CRT i *c* nie jest jedną z tych wartości, funkcje wywołują potwierdzenie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istcntrl**|**iscntrl**|**iscntrl**|**iswcntrl**|
|**_istcntrl_l**|**_iscntrl_l**|**_iscntrl_l**|**_iswcntrl_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**iscntrl**|\<ctype.h>|
|**iswcntrl**|\<CType.h > lub \<wchar.h >|
|**_iscntrl_l**|\<ctype.h>|
|**_iswcntrl_l**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
