---
title: feclearexcept1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc980cea3df0b86848f2cad2b2eceb48bfb2f039
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="feclearexcept"></a>feclearexcept

Próbuje wyczyścić flagi zmiennoprzecinkowych wyjątków argumentu.

## <a name="syntax"></a>Składnia

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*z wyjątkiem*<br/>
Flagi stanu wyjątek wyczyścić.

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli *z wyjątkiem* wynosi zero, lub jeśli określone wyjątki pomyślnie zostały wyczyszczone. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Feclearexcept** funkcja próbuje wyczyścić wartość zmiennoprzecinkowa punkt wyjątek flagi stanu określonego przez *z wyjątkiem*. Funkcja obsługuje makrach wyjątków zdefiniowane w fenv.h:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w wcześniej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Funkcja wymuszono zaokrąglona wyniku przechowywanego wcześniej operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w wcześniej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniej wynik operacji zmiennoprzecinkowej jest zbyt duży, może być reprezentowana.|
|FE_UNDERFLOW|Wynik operacji zmiennoprzecinkowej wcześniej był za mały na pełne precyzji; wartość została utworzona.|
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|

*z wyjątkiem* argument może być zero lub wartość logiczną lub co najmniej jednego z makr wyjątków obsługiwanych. Wynik dowolna inna wartość argumentu jest niezdefiniowany.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
