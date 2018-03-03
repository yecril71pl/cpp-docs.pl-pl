---
title: "_set_output_format — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a0ad6631d9171e8fcdc59e13e60eda2cc729c79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setoutputformat"></a>_set_output_format
Dostosowuje formatów wyjściowych przez sformatowany funkcje We/Wy.  
  
> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned int _set_output_format(  
   unsigned int format  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`format`  
 Wartość reprezentująca formatu do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Poprzednie format danych wyjściowych.  
  
## <a name="remarks"></a>Uwagi  
 `_set_output_format`Służy do konfigurowania dane wyjściowe sformatowany funkcje We/Wy, takich jak [printf_s —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). Obecnie tylko Konwencji formatowania, który może zostać zmieniona przez tę funkcję jest liczbę miejsc po przecinku wyświetlane w wykładniki w danych wyjściowych punktu liczb zmiennoprzecinkowych.  
  
 Domyślnie dane wyjściowe zmiennoprzecinkową punktu numery przez funkcje takie jak `printf_s`, `wprintf_s`, i powiązane funkcje biblioteki Visual C++, C Standard drukuje trzech cyfr dla wykładnik, nawet jeśli trzech cyfr nie są wymagane do reprezentowania wartości wykładnik. Wartości zerowe są używane do konsoli wartość do trzech cyfr. `_set_output_format`Pozwala zmienić to zachowanie, dzięki czemu są podane dwie cyfry wykładnika, chyba że trzecia cyfra jest wymagany przez rozmiar wykładnik.  
  
 Aby włączyć wykładniki dwucyfrowe, wywołanie tej funkcji z parametrem `_TWO_DIGIT_EXPONENT`, jak pokazano w przykładzie. Aby wyłączyć dwóch wykładniki cyfrę, wywołanie tej funkcji z argumentu o wartości 0.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_set_output_format`|\<stdio.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
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
 [printf_s —, _printf_s_l —, wprintf_s — _wprintf_s_l —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_get_output_format](../c-runtime-library/get-output-format.md)