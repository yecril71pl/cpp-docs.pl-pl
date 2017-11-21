---
title: "_fcvt — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fcvt
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
f1_keywords: _fcvt
dev_langs: C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 495460722a72f6002b602336d3a01bff4b9d3af6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fcvt"></a>_fcvt
Konwertuje liczba zmiennoprzecinkowa na ciąg. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_fcvt_s —](../../c-runtime-library/reference/fcvt-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_fcvt(   
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
 Liczba cyfr po punkcie dziesiętnym.  
  
 `dec`  
 Wskaźnik do składowanej położenie punktu dziesiętnego.  
  
 `sign`  
 Wskaźnik do wskaźnika logowania przechowywanej.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_fcvt`Zwraca wskaźnik do ciągu znaków, wartość NULL w przypadku błędu.  
  
## <a name="remarks"></a>Uwagi  
 `_fcvt` Funkcja konwertuje liczba zmiennoprzecinkowa na ciąg znaków zakończony znakiem null. `value` Parametr jest liczbie zmiennoprzecinkowej do skonwertowania. `_fcvt`przechowuje cyfry `value` jako ciąg i dołącza znak null ('\0'). `count` Parametr określa liczbę cyfr po punkcie dziesiętnym przechowywania. Nadmiarowe cyfry są zaokrąglane do `count` miejsca. Jeśli jest dostępnych mniej niż `count` cyfr precyzji, ten ciąg jest uzupełniana zerami z.  
  
 Całkowita liczba cyfr zwrócony przez `_fcvt` nie przekroczy `_CVTBUFSIZE`.  
  
 Tylko cyfry są przechowywane w ciągu. Położenie punktu dziesiętnego i znak `value` można uzyskać z `dec` i zalogować się po wywołaniu. `dec` Parametr wskazuje na wartość całkowitą; daje to wartość całkowita położenie punktu dziesiętnego względem początku ciąg. Wartość zero lub wartość ujemną całkowitą wskazuje dziesiętnego znajduje się na lewo od pierwszą. Parametr `sign` wskazuje na liczbę całkowitą określającą znak `value`. Liczba całkowita jest ustawiony na 0, jeśli `value` jest dodatnia i ma ustawioną wartość różna od zera, jeśli liczba `value` jest ujemna.  
  
 Różnica między `_ecvt` i `_fcvt` jest interpretacji `count` parametru. `_ecvt`interpretuje `count` jako liczba cyfr w ciągu wyjściowego, podczas gdy `_fcvt` interpretuje `count` jako liczbę cyfr po punkcie dziesiętnym.  
  
 `_ecvt`i `_fcvt` do konwersji użyj pojedynczego statycznie przydzielonego buforu. Każde wywołanie do jednej z tych procedur niszczy wyniki poprzedniego wywołania.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `dec` lub `sign` ma wartość NULL, lub `count` wynosi 0, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i zostanie zwrócona wartość NULL.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_fcvt`|\<stdlib.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fcvt.c  
// compile with: /W3  
// This program converts the constant  
// 3.1415926535 to a string and sets the pointer  
// buffer to point to that string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  decimal, sign;  
   char *buffer;  
   double source = 3.1415926535;  
  
   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996  
   // Note: _fcvt is deprecated; consider using _fcvt_s instead  
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",  
            source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [atof —, _atof_l —, _wtof — _wtof_l —](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt —](../../c-runtime-library/reference/ecvt.md)   
 [_gcvt —](../../c-runtime-library/reference/gcvt.md)