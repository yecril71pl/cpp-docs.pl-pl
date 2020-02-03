---
title: fetestexcept
ms.date: 04/05/2018
api_name:
- fetestexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fetestexcept
- fenv/fetestexcept
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: e70ae1b74420b8186cccd8fc8a817423df618adf
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972160"
---
# <a name="fetestexcept"></a>fetestexcept

Określa, które z określonych flag stanu wyjątków zmiennoprzecinkowych są obecnie ustawione.

## <a name="syntax"></a>Składnia

```C
int fetestexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*Oprócz*<br/>
Bitowe lub zmiennoprzecinkowe flagi stanu do przetestowania.

## <a name="return-value"></a>Wartość zwrócona

Po powodzeniu funkcja zwraca maskę bitów zawierającą bitowe lub zmiennoprzecinkowe makra wyjątków, które odpowiadają aktualnie ustawionymi flagami stanu wyjątku. Zwraca wartość 0, jeśli żaden z wyjątków nie jest ustawiony.

## <a name="remarks"></a>Uwagi

Użyj funkcji fetestexcept, aby określić, które wyjątki zostały zgłoszone przez operację zmiennoprzecinkową. Użyj parametru *except* , aby określić, które flagi stanu wyjątku mają zostać przetestowane. Funkcja **fetestexcept** używa tych makr wyjątków zdefiniowanych w \<fenv. h > w *z wyjątkiem* i wartości zwracanej:

|Makro wyjątku|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd Singularity lub wartość w poprzedniej operacji zmiennoprzecinkowej; utworzono nieskończoną wartość.|
|FE_INEXACT|Funkcja była zmuszona do zaokrąglania przechowywanego wyniku poprzedniej operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w poprzedniej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniejszy wynik operacji zmiennoprzecinkowej był zbyt duży, aby można było go przedstawić.|
|FE_UNDERFLOW|Wcześniejszy wynik operacji zmiennoprzecinkowej był zbyt mały, aby mógł być reprezentowany z pełną dokładnością; utworzono nienormalną wartość.|
|FE_ALL_EXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|

Określony argument *except* może mieć wartość 0, jedno z obsługiwanych makr wyjątków zmiennoprzecinkowych lub bitowe lub dwa lub więcej makr. Efekt każdej innej *z wyjątkiem* wartości argumentu jest niezdefiniowany.

Aby użyć tej funkcji, należy wyłączyć optymalizacje zmiennoprzecinkowe, które mogą uniemożliwić dostęp przy użyciu dyrektywy `#pragma fenv_access(on)` przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
