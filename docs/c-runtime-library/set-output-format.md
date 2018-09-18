---
title: _set_output_format — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _set_output_format
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- set_output_format
- _set_output_format
dev_langs:
- C++
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9d41ae92a829452edebe390723997a67b5cd812
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112073"
---
# <a name="setoutputformat"></a>_set_output_format

Dostosowuje formaty danych wyjściowych używane przez funkcje sformatowane we/wy.

> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>Parametry

*Format*<br/>
[in] Wartość reprezentująca formatu do użycia.

## <a name="return-value"></a>Wartość zwracana

Poprzednie format danych wyjściowych.

## <a name="remarks"></a>Uwagi

`_set_output_format` Służy do konfigurowania dane wyjściowe sformatowane funkcje We/Wy, takich jak [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). Obecnie jedyną Konwencji formatowania, która może zostać zmieniona przez tę funkcję, jest liczbę cyfr wyświetlanych w wykładniki w danych wyjściowych liczb zmiennoprzecinkowych.

Domyślnie dane wyjściowe pływających punktu numery przez funkcje takie jak `printf_s`, `wprintf_s`, i powiązane funkcje biblioteki standardowej C Visual C++ drukuje trzy cyfry wykładnika potęgi, nawet jeśli trzech cyfr nie są wymagane do reprezentowania wartości obiektu wykładnik potęgi. Wartości zerowe są używane do wypełnienia wartości do trzech cyfr. `_set_output_format` Pozwala zmienić to zachowanie, aby były drukowane tylko dwie cyfry wykładnika, chyba że trzecia cyfra jest wymagana przez rozmiar wykładnik potęgi.

Aby włączyć wykładniki dwóch cyfr, wywołaj tę funkcję, za pomocą parametru `_TWO_DIGIT_EXPONENT`, jak pokazano w przykładzie. Aby wyłączyć dwie cyfry wykładniki, wywołaj tę funkcję, z nieprawidłowym argumentem 0.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wstępie.

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