---
title: "_gcvt_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _gcvt_s
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
- _gcvt_s
- gcvt_s
dev_langs: C++
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7ba9f1a7a77c0f9d23423906c18b05ace5b20ec8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="gcvts"></a>_gcvt_s
Konwertuje wartość zmiennoprzecinkowa na ciąg. To jest wersja [_gcvt —](../../c-runtime-library/reference/gcvt.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _gcvt_s(   
   char *buffer,  
   size_t sizeInBytes,  
   double value,  
   int digits   
);  
template <size_t cchStr>  
errno_t _gcvt_s(   
   char (&buffer)[cchStr],  
   double value,  
   int digits   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Bufor do przechowywania wynik konwersji.  
  
 [in]`sizeInBytes`  
 Rozmiar buforu.  
  
 [in]`value`  
 Wartość do skonwertowania.  
  
 [in]`digits`  
 Liczba cyfr znaczących przechowywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie. Jeśli wystąpi błąd z powodu nieprawidłowego parametru (patrz poniższa tabela nieprawidłowe wartości), program obsługi nieprawidłowych parametrów jest wywoływany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, zostanie zwrócony kod błędu. Kody błędów są definiowane w Errno.h. Aby uzyskać listę tych błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`buffer`|`sizeInBytes`|`value`|`digits`|Zwraca|Wartość w`buffer`|  
|--------------|-------------------|-------------|--------------|------------|-----------------------|  
|`NULL`|wszystkie|wszystkie|wszystkie|`EINVAL`|Nie modyfikować.|  
|nie `NULL` (wskazuje prawidłowy pamięci)|zero|wszystkie|wszystkie|`EINVAL`|Nie modyfikować.|  
|nie `NULL` (wskazuje prawidłowy pamięci)|wszystkie|wszystkie|>= `sizeInBytes`|`EINVAL`|Nie modyfikować.|  
  
 **Problemy z zabezpieczeniami**  
  
 `_gcvt_s`można wygenerować naruszenia zasad dostępu, jeśli `buffer` nie wskazuje na prawidłową pamięci i nie jest `NULL`.  
  
## <a name="remarks"></a>Uwagi  
 `_gcvt_s` Funkcja konwertuje zmiennoprzecinkowe `value` na ciąg znaków (w tym punktem dziesiętnym i bajtów możliwości logowania) i zapisuje ciąg w `buffer`. `buffer`powinien być wystarczająco duży, aby pomieścić skonwertowana wartość plus znak końcowy null, które są automatycznie dołączane. Bufor o długości `_CVTBUFSIZE` jest wystarczająca dla dowolnej liczby zmiennoprzecinkowe wartości. Jeśli rozmiar buforu `digits` + 1 jest używany, funkcja nie zastąpi końcu buforu, dlatego należy podać wystarczające buforu dla tej operacji. `_gcvt_s`próbuje utworzyć `digits` cyfr w formacie dziesiętnym. Jeśli nie, tworzy `digits` cyfr w notacji wykładniczej. Końcowe zera można pominąć w konwersji.  
  
 W języku C++ za pomocą tej funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążenie można wnioskować o długości buforu automatycznie, eliminując konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Wersja do debugowania tej funkcji po raz pierwszy wypełnia bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_gcvt_s`|\<stdlib.h >|\<Error.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_gcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char buf[_CVTBUFSIZE];  
  int decimal;  
  int sign;  
  int err;  
  
  err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);  
  
  if (err != 0)  
  {  
     printf("_gcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 1.2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [atof —, _atof_l —, _wtof — _wtof_l —](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt_s —](../../c-runtime-library/reference/ecvt-s.md)   
 [_fcvt_s —](../../c-runtime-library/reference/fcvt-s.md)   
 [_gcvt —](../../c-runtime-library/reference/gcvt.md)