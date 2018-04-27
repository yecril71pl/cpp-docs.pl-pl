---
title: wctrans — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wctrans
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctrans
dev_langs:
- C++
helpviewer_keywords:
- character codes, wctrans
- characters, codes
- characters, converting
- wctrans function
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dab0f5a55f9ee1df30b0a5f040e7944292b5cf25
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="wctrans"></a>wctrans

Określa mapowanie jeden zestaw kodów znaków do innego.

## <a name="syntax"></a>Składnia

```C
wctrans_t wctrans(
   const char *property
);
```

### <a name="parameters"></a>Parametry

*właściwość*<br/>
Ciąg, który określa jeden prawidłowy przekształcenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **lc_ctype —** kategorii bieżące ustawienia regionalne nie definiuje mapowanie, którego nazwa odpowiada właściwości ciągu *właściwości*, funkcja zwraca wartość zero. W przeciwnym razie zwraca wartość niezerową odpowiednie do użycia jako drugi argument do kolejne wywołanie [towctrans —](towctrans.md).

## <a name="remarks"></a>Uwagi

Ta funkcja określa mapowanie jeden zestaw kodów znaków do innego.

Następujące pary wywołań ma takie samo zachowanie wszystkich ustawień regionalnych, ale można zdefiniować dodatkowe mapowania nawet zgodnie z ustawieniami regionalnymi "C":

|Funkcja|Identyczny|
|--------------|-------------|
|tolower(c)|towctrans — (c, wctrans("towlower"))|
|towupper(c)|towctrans — (c, wctrans("toupper"))|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctrans**|\<wctype.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_wctrans.cpp
// compile with: /EHsc
// This example determines a mapping from one set of character
// codes to another.

#include <wchar.h>
#include <wctype.h>
#include <stdio.h>
#include <iostream>

int main()
{
    wint_t c = 'a';
    printf_s("%d\n",c);

    wctrans_t i = wctrans("toupper");
    printf_s("%d\n",i);

    wctrans_t ii = wctrans("towlower");
    printf_s("%d\n",ii);

    wchar_t wc = towctrans(c, i);
    printf_s("%d\n",wc);
}
```

```Output
97
1
0
65
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
