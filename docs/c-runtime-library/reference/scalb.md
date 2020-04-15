---
title: _scalb, _scalbf
ms.date: 4/2/2020
api_name:
- _scalb
- _scalbf
- _o__scalb
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
ms.openlocfilehash: 6501fe53e67d0f277fa64c08e0edbff1d7eeb61a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332685"
---
# <a name="_scalb-_scalbf"></a>_scalb, _scalbf

Skaluje argument o mocy 2.

## <a name="syntax"></a>Składnia

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>Parametry

*X*<br/>
Podwójna precyzja, wartość zmiennoprzecinowa.

*Exp*<br/>
Wykładnik długiej liczby całkowitej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą, jeśli zakończy się pomyślnie. Przy przepełnienie (w zależności od znaku *x),* **_scalb** zwraca +/- **HUGE_VAL**; zmienna **errno** jest ustawiona na **ERANGE**.

Aby uzyskać więcej informacji na temat tego i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_scalb** oblicza wartość *x* \* 2<sup>*exp*</sup>.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_scalb** **, _scalbf**|\<> float.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
