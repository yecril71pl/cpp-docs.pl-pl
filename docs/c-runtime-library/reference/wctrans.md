---
title: wctrans
ms.date: 11/04/2016
api_name:
- wctrans
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctrans
helpviewer_keywords:
- character codes, wctrans
- characters, codes
- characters, converting
- wctrans function
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
ms.openlocfilehash: a75de3b699d0eb5ec6117d0f627e6a8ba34dbc62
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944889"
---
# <a name="wctrans"></a>wctrans

Określa mapowanie z jednego zestawu kodów znaków na inny.

## <a name="syntax"></a>Składnia

```C
wctrans_t wctrans(
   const char *property
);
```

### <a name="parameters"></a>Parametry

*właściwość*<br/>
Ciąg określający jeden z prawidłowych transformacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli kategoria **LC_CTYPE** bieżących ustawień regionalnych nie definiuje mapowania, którego nazwa jest zgodna z *właściwością*ciągu właściwości, funkcja zwraca wartość zero. W przeciwnym razie zwraca wartość różną od zera odpowiednią do użycia jako drugi argument dla kolejnego wywołania do [towctrans](towctrans.md).

## <a name="remarks"></a>Uwagi

Ta funkcja Określa mapowanie z jednego zestawu kodów znaków na inny.

Poniższe pary wywołań mają takie samo zachowanie we wszystkich ustawieniach regionalnych, ale można zdefiniować dodatkowe mapowania nawet w ustawieniach regionalnych "C":

|Funkcja|Tak samo jak|
|--------------|-------------|
|ToLower (c)|towctrans (c, wctrans ("towlower"))|
|towupper (c)|towctrans (c, wctrans ("ToUpper"))|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctrans**|\<wctype.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
