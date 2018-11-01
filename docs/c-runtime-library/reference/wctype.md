---
title: wctype
ms.date: 11/04/2016
apiname:
- wctype
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
apitype: DLLExport
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: 81caf8e1ab04635d205d7b01af2d4c2896eec01c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456904"
---
# <a name="wctype"></a>wctype

Określa reguły klasyfikacji, aby poznać kody znaków dwubajtowych.

## <a name="syntax"></a>Składnia

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Parametry

*właściwość*<br/>
Właściwość ciągu.

## <a name="return-value"></a>Wartość zwracana

Jeśli **LC_CTYPE** kategorii bieżących ustawień regionalnych nie definiuje reguły klasyfikacji, w których nazwa pasuje do ciągu właściwość *właściwość*, funkcja zwraca wartość zero. W przeciwnym razie zwraca wartość różną od zera odpowiedni do użytku jako drugi argument na kolejne wywołanie [towctrans —](towctrans.md).

## <a name="remarks"></a>Uwagi

Funkcja określa reguły klasyfikacji, aby poznać kody znaków dwubajtowych. Następujące pary wywołania mają takie samo zachowanie we wszystkich ustawieniach regionalnych (ale implementację można zdefiniować reguły klasyfikacji dodatkowe nawet w przypadku ustawień regionalnych "C"):

|Funkcja|Takie same jak|
|--------------|-------------|
|iswalnum(c)|iswctype (c, wctype ("alnum"))|
|iswalpha(c)|iswctype (c, wctype ("Alfa"))|
|iswcntrl(c)|iswctype (c, wctype ("CTRL"))|
|iswdigit(c)|iswctype (c, wctype ("digit"))|
|iswgraph(c)|iswctype (c, wctype ("wykres"))|
|iswlower(c)|iswctype (c, wctype ("małe"))|
|iswprint(c)|iswctype (c, wctype ("print")")|
|iswpunct(c)|iswctype (c, wctype ("punct"))|
|iswspace(c)|iswctype (c, wctype ("space"))|
|iswupper(c)|iswctype (c, wctype ("górnego"))|
|iswxdigit(c)|iswctype (c, wctype ("xdigit"))|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
