---
title: _set_output_format
ms.date: 11/04/2016
api_name:
- _set_output_format
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_output_format
- _set_output_format
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
ms.openlocfilehash: c855df4c29a53fd898b920f6446afe4e568ba5bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360917"
---
# <a name="_set_output_format"></a>_set_output_format

Dostosowuje formaty wyjściowe używane przez sformatowane funkcje we/wy.

> [!IMPORTANT]
> Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>Parametry

*Formacie*<br/>
[w] Wartość reprezentująca format do użycia.

## <a name="return-value"></a>Wartość zwracana

Poprzedni format wyjściowy.

## <a name="remarks"></a>Uwagi

`_set_output_format`służy do konfigurowania danych wyjściowych sformatowanych funkcji we/wy, takich jak [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). Obecnie jedyną konwencją formatowania, którą można zmienić za pomocą tej funkcji, jest liczba cyfr wyświetlanych w wykładnikach w danych wyjściowych liczb zmiennoprzecinkowych.

Domyślnie dane wyjściowe liczb zmiennoprzecinkowych według funkcji, takich jak `printf_s`, `wprintf_s`i powiązanych funkcji w visual C++ Standard C biblioteki drukuje trzy cyfry wykładnika, nawet jeśli trzy cyfry nie są wymagane do reprezentowania wartości wykładnika. Zera są używane do wyładowywać wartość do trzech cyfr. `_set_output_format`umożliwia zmianę tego zachowania tak, aby tylko dwie cyfry były drukowane w wykładniczym, chyba że trzecia cyfra jest wymagana przez rozmiar wykładnika.

Aby włączyć wykładniki dwucyfrowe, należy wywołać `_TWO_DIGIT_EXPONENT`tę funkcję z parametrem , jak pokazano w przykładzie. Aby wyłączyć wykładniki dwucyfrowe, należy wywołać tę funkcję z argumentem 0.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../c-runtime-library/compatibility.md) we wstępie.

## <a name="example"></a>Przykład

```C
// crt_set_output_format.c
#include <stdio.h>

void printvalues(double x, double y)
{
   printf_s("%11.4e %11.4e\n", x, y);
   printf_s("%11.4E %11.4E\n", x, y);
   printf_s("%11.4g %11.4g\n", x, y);
   printf_s("%11.4G %11.4G\n", x, y);
}

int main()
{
   double x = 1.211E-5;
   double y = 2.3056E-112;
   unsigned int old_exponent_format;

   // Use the default format
   printvalues(x, y);

   // Enable two-digit exponent format
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);

   printvalues(x, y);

   // Disable two-digit exponent format
   _set_output_format( old_exponent_format );

   printvalues(x, y);
}
```

```Output
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
1.2110e-05 2.3056e-112
1.2110E-05 2.3056E-112
  1.211e-05  2.306e-112
  1.211E-05  2.306E-112
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
```

## <a name="see-also"></a>Zobacz też

[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
