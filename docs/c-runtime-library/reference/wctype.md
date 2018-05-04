---
title: wctype — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bb5003db02ed27c2906ebc3619313489e40e5fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="wctype"></a>wctype

Określa reguły klasyfikacji kodów znaków dwubajtowych.

## <a name="syntax"></a>Składnia

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Parametry

*właściwość*<br/>
Ciąg właściwości.

## <a name="return-value"></a>Wartość zwracana

Jeśli **lc_ctype —** kategorii bieżące ustawienia regionalne nie definiuje reguły klasyfikacji, którego nazwa odpowiada właściwości ciągu *właściwości*, funkcja zwraca wartość zero. W przeciwnym razie zwraca wartość niezerową odpowiednie do użycia jako drugi argument do kolejne wywołanie [towctrans —](towctrans.md).

## <a name="remarks"></a>Uwagi

Funkcja Określa regułę klasyfikacji kodów znaków dwubajtowych. Następujące pary wywołań ma takie samo zachowanie wszystkich ustawień regionalnych (ale implementacja można zdefiniować reguły klasyfikacji dodatkowe nawet zgodnie z ustawieniami regionalnymi "C"):

|Funkcja|Identyczny|
|--------------|-------------|
|iswalnum(c)|iswctype — wctype (c — ("alnum"))|
|iswalpha(c)|iswctype — wctype (c — ("Alfa"))|
|iswcntrl(c)|iswctype — wctype (c — ("CTRL"))|
|iswdigit(c)|iswctype — wctype (c — ("cyfr"))|
|iswgraph(c)|iswctype — wctype (c — ("wykresu"))|
|iswlower(c)|iswctype — wctype (c — ("niżej"))|
|iswprint(c)|iswctype — wctype (c — ("print"))|
|iswpunct(c)|iswctype — wctype (c — ("punct"))|
|iswspace(c)|iswctype — wctype (c — ("miejsca"))|
|iswupper(c)|iswctype — wctype (c — ("górna"))|
|iswxdigit(c)|iswctype — wctype (c — ("xdigit"))|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
