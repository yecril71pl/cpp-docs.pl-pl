---
title: "_ecvt_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _ecvt_s
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
- ecvt_s
- _ecvt_s
dev_langs: C++
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d835b45d9f06b9b8ff59916e36b124f8b1ec848d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ecvts"></a>_ecvt_s
Konwertuje `double` numer na ciąg. To jest wersja [_ecvt —](../../c-runtime-library/reference/ecvt.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _ecvt_s(   
   char * _Buffer,  
   size_t _SizeInBytes,  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
);  
template <size_t size>  
errno_t _ecvt_s(   
   char (&_Buffer)[size],  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`_Buffer`  
 Wypełniony wskaźnika na ciąg cyfr, wynik konwersji.  
  
 [in]`_SizeInBytes`  
 Rozmiar buforu w bajtach.  
  
 [in]`_Value`  
 Numer do skonwertowania.  
  
 [in]`_Count`  
 Liczba cyfr przechowywane.  
  
 [out]`_Dec`  
 Przechowywane położenie punktu dziesiętnego.  
  
 [out]`_Sign`  
 Znak przekonwertowany numer.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu w przypadku awarii. Kody błędów są definiowane w Errno.h. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 W przypadku nieprawidłowy parametr wymienionych w poniższej tabeli, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `EINVAL`.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`_Buffer`|`_SizeInBytes`|_Value|_Count|_Dec|_Zaloguj|Wartość zwracana|Wartość w`buffer`|  
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|  
|`NULL`|wszystkie|wszystkie|wszystkie|wszystkie|wszystkie|`EINVAL`|Nie modyfikować.|  
|nie `NULL` (wskazuje prawidłowy pamięci)|<=0|wszystkie|wszystkie|wszystkie|wszystkie|`EINVAL`|Nie modyfikować.|  
|wszystkie|wszystkie|wszystkie|wszystkie|`NULL`|wszystkie|`EINVAL`|Nie modyfikować.|  
|wszystkie|wszystkie|wszystkie|wszystkie|wszystkie|`NULL`|`EINVAL`|Nie modyfikować.|  
  
 **Problemy z zabezpieczeniami**  
  
 `_ecvt_s`może generować naruszenia zasad dostępu, jeśli `buffer` nie wskazuje na prawidłową pamięci i nie jest `NULL`.  
  
## <a name="remarks"></a>Uwagi  
 `_ecvt_s` Funkcja konwertuje liczba zmiennoprzecinkowa na ciąg znaków. `_Value` Parametr jest liczbie zmiennoprzecinkowej do skonwertowania. Ta funkcja przechowuje do `count` cyfr `_Value` jako ciąg i dołącza znak null ('\0'). Jeśli liczba cyfr w `_Value` przekracza `_Count`, cyfrę znaczącymi bitami jest zaokrąglana. Jeśli jest dostępnych mniej niż `count` cyfr, ten ciąg jest uzupełniana zerami z.  
  
 Tylko cyfry są przechowywane w ciągu. Położenie punktu dziesiętnego i znak `_Value` można uzyskać od `_Dec` i `_Sign` po wywołaniu. `_Dec` Parametr wskazuje wartość całkowitą, podając położenie punktu dziesiętnego względem początku ciąg. Wartość liczby całkowitej 0 ani ujemna wskazuje dziesiętnego znajduje się na lewo od pierwszej cyfry. `_Sign` Parametr wskazuje na liczbę całkowitą wskazującą znak liczby przekonwertowany. Jeśli wartość całkowita ma wartość 0, liczba jest dodatnia. W przeciwnym razie liczba jest ujemna.  
  
 Bufor o długości `_CVTBUFSIZE` jest wystarczająca dla wartości zmiennoprzecinkowych.  
  
 Różnica między `_ecvt_s` i `_fcvt_s` jest interpretacji `_Count` parametru. `_ecvt_s`interpretuje `_Count` jako liczba cyfr w ciągu wyjściowego, podczas gdy `_fcvt_s` interpretuje `_Count` jako liczbę cyfr po punkcie dziesiętnym.  
  
 W języku C++ za pomocą tej funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążenie można wnioskować o długości buforu automatycznie, eliminując konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Wersja do debugowania tej funkcji po raz pierwszy wypełnia bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|  
|--------------|---------------------|---------------------|  
|`_ecvt_s`|\<stdlib.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// ecvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( )  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_ecvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 12000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [atof —, _atof_l —, _wtof — _wtof_l —](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt —](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt_s —](../../c-runtime-library/reference/fcvt-s.md)   
 [_gcvt_s —](../../c-runtime-library/reference/gcvt-s.md)