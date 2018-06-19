---
title: _ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbcpunct_l
- _ismbcblank
- _ismbcprint
- _ismbcgraph_l
- _ismbcblank_l
- _ismbcpunct
- _ismbcprint_l
- _ismbcspace_l
- _ismbcspace
- _ismbcgraph
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
- _ismbcspace
- _ismbcgraph
- _ismbcpunct
- ismbcspace_l
- ismbcgraph
- _ismbcgraph_l
- _ismbcprint
- _ismbcspace_l
- ismbcprint
- ismbcgraph_l
- ismbcspace
- ismbcpunct
dev_langs:
- C++
helpviewer_keywords:
- ismbcspace_l function
- _ismbcprint_l function
- ismbcspace function
- ismbcpunct function
- _ismbcspace_l function
- _ismbcprint function
- ismbcprint function
- _ismbcgraph function
- ismbcgraph_l function
- _ismbcpunct_l function
- ismbcpunct_l function
- ismbcprint_l function
- _ismbcpunct function
- ismbcgraph function
- _ismbcgraph_l function
- _ismbcspace function
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da9231dcf64222aa075194f72892896972e2abf7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405500"
---
# <a name="ismbcgraph-ismbcgraphl-ismbcprint-ismbcprintl-ismbcpunct-ismbcpunctl-ismbcblank-ismbcblankl-ismbcspace-ismbcspacel"></a>_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l

Określa, czy znak jest znak graficzny znak wyświetlania, znak interpunkcyjny albo znak odstępu.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbcgraph(
   unsigned int c
);
int _ismbcgraph_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcprint(
   unsigned int c
);
int _ismbcprint_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcpunct(
   unsigned int c
);
int _ismbcpunct_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcblank(
   unsigned int c
);
int _ismbcblank_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcspace(
   unsigned int c
);
int _ismbcspace_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Można określić znak.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każdy z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli jej nie ma. Jeśli *c* < = 255 i ma odpowiadającego **_ismbb —** procedura (na przykład **_ismbcalnum —** odpowiada **_ismbbalnum —**), wynik jest zwracana wartość odpowiadającego **_ismbb —** procedury.

Wersje te funkcje są identyczne, z tą różnicą, że te, które mają **_l** sufiks Użyj ustawień regionalnych, których jest przekazywany w ich zachowania zależnych od ustawień regionalnych, zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji testy danego znaków wielobajtowych dla podanego warunku.

|Procedura|Stan testu|Przykład kodu strony 932|
|-------------|--------------------|---------------------------|
|**_ismbcgraph**|Grafika|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* odzwierciedla jednobajtowe znaków ASCII lub katakana drukowania z wyjątkiem (biały znak).|
|**_ismbcprint**|Do druku|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* odzwierciedla jednobajtowe ASCII lub katakana drukowalnych znaków włącznie (biały znak).|
|**_ismbcpunct**|Znaki interpunkcyjne|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* odzwierciedla jednobajtowe ASCII lub katakana znak interpunkcyjny.|
|**_ismbcblank**|Spację lub tabulator poziomy|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* jest spację lub tabulator poziomy: *c*= 0x20 lub *c*= 0x09.|
|**_ismbcspace**|Biały znak|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy *c* jest biały znak: *c*= 0x20 lub 0x09 < =*c*< = 0x0D.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbcgraph**|\<mbstring.h>|
|**_ismbcgraph_l**|\<mbstring.h>|
|**_ismbcprint**|\<mbstring.h>|
|**_ismbcprint_l**|\<mbstring.h>|
|**_ismbcpunct**|\<mbstring.h>|
|**_ismbcpunct_l**|\<mbstring.h>|
|**_ismbcblank**|\<mbstring.h>|
|**_ismbcblank_l**|\<mbstring.h>|
|**_ismbcspace**|\<mbstring.h>|
|**_ismbcspace_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
