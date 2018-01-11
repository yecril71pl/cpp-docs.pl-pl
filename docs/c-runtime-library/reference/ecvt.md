---
title: "_ecvt — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _ecvt
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
f1_keywords: _ecvt
dev_langs: C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 237924bce3bb4b659e72cec060738035d91c7cbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ecvt"></a>_ecvt
Konwertuje `double` numer na ciąg. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_ecvt_s —](../../c-runtime-library/reference/ecvt-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_ecvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Numer do skonwertowania.  
  
 `count`  
 Liczba cyfr przechowywane.  
  
 `dec`  
 Przechowywane położenie punktu dziesiętnego.  
  
 `sign`  
 Znak przekonwertowany numer.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_ecvt`Zwraca wskaźnik do ciąg cyfr; Wartość NULL, jeśli wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_ecvt` Funkcja konwertuje liczba zmiennoprzecinkowa na ciąg znaków. `value` Parametr jest liczbie zmiennoprzecinkowej do skonwertowania. Ta funkcja przechowuje do `count` cyfr `value` jako ciąg i dołącza znak null ('\0'). Jeśli liczba cyfr w `value` przekracza `count`, cyfrę znaczącymi bitami jest zaokrąglana. Jeśli jest dostępnych mniej niż `count` cyfr, ten ciąg jest uzupełniana zerami z.  
  
 Całkowita liczba cyfr zwrócony przez `_ecvt` nie przekroczy `_CVTBUFSIZE`.  
  
 Tylko cyfry są przechowywane w ciągu. Położenie punktu dziesiętnego i znak `value` można uzyskać od `dec` i `sign` po wywołaniu. `dec` Parametr wskazuje wartość całkowitą, podając położenie punktu dziesiętnego względem początku ciąg. Wartość liczby całkowitej 0 ani ujemna wskazuje dziesiętnego znajduje się na lewo od pierwszej cyfry. `sign` Parametr wskazuje na liczbę całkowitą wskazującą znak liczby przekonwertowany. Jeśli wartość całkowita ma wartość 0, liczba jest dodatnia. W przeciwnym razie liczba jest ujemna.  
  
 Różnica między `_ecvt` i `_fcvt` jest interpretacji `count` parametru. `_ecvt`interpretuje `count` jako liczba cyfr w ciągu wyjściowego, podczas gdy `_fcvt` interpretuje `count` jako liczbę cyfr po punkcie dziesiętnym.  
  
 `_ecvt`i `_fcvt` do konwersji użyj pojedynczego statycznie przydzielonego buforu. Każde wywołanie do jednej z tych procedur niszczy wynik poprzedniego wywołania.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `dec` lub `sign` ma wartość NULL, lub `count` wynosi 0, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i zostanie zwrócona wartość NULL.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_ecvt`|\<stdlib.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_ecvt.c  
// compile with: /W3  
// This program uses _ecvt to convert a  
// floating-point number to a character string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int     decimal,   sign;  
   char    *buffer;  
   int     precision = 10;  
   double  source = 3.1415926535;  
  
   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996  
   // Note: _ecvt is deprecated; consider using _ecvt_s instead  
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",  
           source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [atof —, _atof_l —, _wtof — _wtof_l —](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_fcvt —](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)