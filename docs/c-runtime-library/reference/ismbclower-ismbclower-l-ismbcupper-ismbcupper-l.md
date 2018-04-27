---
title: _ismbclower —, _ismbclower_l —, _ismbcupper —, _ismbcupper_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- _ismbcupper
- _ismbclower
dev_langs:
- C++
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2350e8f3034d18dda32f3007d714d532828ee338
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Sprawdza, czy znaków wielobajtowych małe lub wielkie litery.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do sprawdzenia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każdy z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli jej nie ma. Jeśli *c*< = 255 i ma odpowiadającego **_ismbb —** procedura (na przykład **_ismbcalnum —** odpowiada **_ismbbalnum —**), wynik jest zwracana wartość odpowiadającego **_ismbb —** procedury.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji testy danego znaków wielobajtowych dla podanego warunku.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby były używane ustawienia regionalne przekazana zamiast bieżące ustawienia regionalne dla ich działania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

|Procedura|Stan testu|Przykład kodu strony 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Małe litery|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* odzwierciedla jednobajtowe małe litery angielskie ASCII: 0x61 < =*c*< = 0x7A.|
|**_ismbclower_l**|Małe litery|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* odzwierciedla jednobajtowe małe litery angielskie ASCII: 0x61 < =*c*< = 0x7A.|
|**_ismbcupper —**|Wielkie litery|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* odzwierciedla jednobajtowe wielkiej litery angielskie ASCII: 0x41 < =*c*< = 0x5A.|
|**_ismbcupper_l**|Wielkie litery|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* odzwierciedla jednobajtowe wielkiej litery angielskie ASCII: 0x41 < =*c*< = 0x5A.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper —**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
