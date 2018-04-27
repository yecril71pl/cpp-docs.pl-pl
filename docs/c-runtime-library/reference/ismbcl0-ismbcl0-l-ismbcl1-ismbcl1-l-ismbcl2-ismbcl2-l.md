---
title: _ismbcl0 —, _ismbcl0_l —, _ismbcl1 —, _ismbcl1_l —, _ismbcl2 —, _ismbcl2_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ismbcl2
- _ismbcl1
- _ismbcl0
- _ismbcl2_l
- _ismbcl1_l
- _ismbcl0_l
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
- ismbcl0
- _ismbcl1_l
- _ismbcl0
- ismbcl1
- ismbcl0_l
- _ismbcl2_l
- ismbcl2
- ismbcl1_l
- _ismbcl1
- _ismbcl0_l
- _ismbcl2
- ismbcl2_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbcl0_l function
- _ismbcl2 function
- _ismbcl1_l function
- ismbcl2 function
- _ismbcl1 function
- ismbcl0_l function
- ismbcl2_l function
- ismbcl1_l function
- ismbcl0 function
- ismbcl1 function
- _ismbcl2_l function
- _ismbcl0 function
ms.assetid: ee15ebd1-462c-4a43-95f3-6735836d626a
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4cbca36f0b396bd0623fee3a4039c20cee3d367c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="ismbcl0-ismbcl0l-ismbcl1-ismbcl1l-ismbcl2-ismbcl2l"></a>_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l

**Kod funkcji strony 932 właściwych**, przy użyciu bieżących ustawień regionalnych lub określona kategoria Stan konwersji lc_ctype —.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbcl0(
   unsigned int c
);
int _ismbcl0_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcl1(
   unsigned int c
);
int _ismbcl1_l(
   unsigned int c ,
   _locale_t locale
);
int _ismbcl2(
   unsigned int c
);
int _ismbcl2_l(
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

Każdy z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli jej nie ma. Jeśli *c* < = 255 i ma odpowiadającego **_ismbb —** procedura (na przykład **_ismbcalnum —** odpowiada **_ismbbalnum —**), wynik jest zwracana wartość odpowiadającego **_ismbb —** procedury.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji testy danego znaków wielobajtowych dla podanego warunku.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

|Procedura|Testowanie warunku (strona kodowa 932 tylko)|
|-------------|-------------------------------------------|
|**_ismbcl0**|Z systemem innym niż Kanji JIS: 0x8140 < =*c*< = 0x889E.|
|**_ismbcl0_l**|Z systemem innym niż Kanji JIS: 0x8140 < =*c*< = 0x889E.|
|**_ismbcl1**|Poziomem JIS-1: 0x889F < =*c*< = 0x9872.|
|**_ismbcl1_l**|Poziomem JIS-1: 0x889F < =*c*< = 0x9872.|
|**_ismbcl2**|Poziomem JIS-2: 0x989F < =*c*< = 0xEAA4.|
|**_ismbcl2_l**|Poziomem JIS-2: 0x989F < =*c*< = 0xEAA4.|

Funkcje Sprawdź, czy określona wartość *c* dopasowań w warunkach opisanych powyżej, ale nie Sprawdź, czy *c* jest prawidłowym znakiem wielobajtowe. Jeśli niższy bajt jest w zakresach 0x00-0x3F, 0x7F lub 0xFD - 0xFF, te zwracają wartość różną od zera, wskazującą, czy znak spełnia warunek testu. Użyj [_ismbbtrail —](ismbbtrail-ismbbtrail-l.md) Aby sprawdzić, czy znaków wielobajtowych jest zdefiniowany.

**Strony 932 określonego kodu zakończenia**

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbcl0**|\<mbstring.h>|
|**_ismbcl0_l**|\<mbstring.h>|
|**_ismbcl1**|\<mbstring.h>|
|**_ismbcl1_l**|\<mbstring.h>|
|**_ismbcl2**|\<mbstring.h>|
|**_ismbcl2_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
