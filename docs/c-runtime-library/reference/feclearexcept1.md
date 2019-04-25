---
title: feclearexcept1
ms.date: 04/05/2018
apiname:
- feclearexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 3c2f037a5be903fc006debfa7319c483431fdd92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334739"
---
# <a name="feclearexcept"></a>feclearexcept

Podejmuje próbę wyczyszczenia flagi wyjątków zmiennoprzecinkowych, określonego przez argument.

## <a name="syntax"></a>Składnia

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*z wyjątkiem*<br/>
Flagi stanu wyjątku do wyczyszczenia.

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli *z wyjątkiem* wynosi zero, czy określone wyjątki zostały pomyślnie wyczyszczone. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Feclearexcept** próbuje funkcja wyczyść wartość zmiennoprzecinkowa punkt flagi stanu wyjątku określonego przez *z wyjątkiem*. Funkcja obsługuje te makra wyjątków, zdefiniowane w fenv.h:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w starszej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Wymuszono funkcji round przechowywanych wynikiem wcześniejszych operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w starszej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wynik operacji zmiennoprzecinkowej wcześniej była zbyt duża, aby mogły być reprezentowane.|
|FE_UNDERFLOW|Wcześniej wyniku operacji zmiennoprzecinkowej był za mały, aby mogły być reprezentowane w o pełnej dokładności; wartość została utworzona.|
|FE_ALL_EXCEPT|Bitowe OR wszystkich obsługiwane wyjątki zmiennoprzecinkowe.|

*z wyjątkiem* argument może być zero lub logiczną lub co najmniej jednego z makr wyjątków obsługiwanych. Wynik jakakolwiek inna wartość argumentu jest niezdefiniowane.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
