---
title: fetestexcept | Dokumentacja firmy Microsoft
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
- fetestexcept
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
- fetestexcept
- fenv/fetestexcept
dev_langs:
- C++
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 599c60134f9c509fd14087bafba79cd9b73ccaa6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fetestexcept"></a>fetestexcept

Określa, które flagi stanu określony wyjątek zmiennoprzecinkowy, którego obecnie są ustawione.

## <a name="syntax"></a>Składnia

```C
int fetestexcept(
   int excepts
);

```

### <a name="parameters"></a>Parametry

*z wyjątkiem*<br/>
Bitowe lub flagi stanu zmiennoprzecinkowe do testowania.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia zwraca maski bitowej zawierającego bitowe lub makra zmiennoprzecinkowych wyjątków, które odpowiadają flagi stanu wyjątek aktualnie ustawiona. Zwraca wartość 0, jeśli żadna z wyjątki są ustawione.

## <a name="remarks"></a>Uwagi

Użyj funkcji fetestexcept, aby określić wyjątki, które zostały zgłoszone przez zmiennoprzecinkową punktu operacji. Użyj *z wyjątkiem* parametr, aby określić flagi stanu wyjątek testu. **Fetestexcept** funkcja używa tych makr wyjątków zdefiniowane w \<fenv.h > w *z wyjątkiem* i zwracana wartość:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w wcześniej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Funkcja wymuszono zaokrąglona wyniku przechowywanego wcześniej operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w wcześniej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniej wynik operacji zmiennoprzecinkowej jest zbyt duży, może być reprezentowana.|
|FE_UNDERFLOW|Wynik operacji zmiennoprzecinkowej wcześniej był za mały na pełne precyzji; wartość została utworzona.|
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|

Określony *z wyjątkiem* argument może mieć wartość 0, jednej z makr wyjątków dotyczących liczb zmiennoprzecinkowych obsługiwanych lub operatora testu koniunkcji lub dwóch lub więcej makr. Efekt wszelkich innych *z wyjątkiem* wartość argumentu jest niezdefiniowany.

Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
