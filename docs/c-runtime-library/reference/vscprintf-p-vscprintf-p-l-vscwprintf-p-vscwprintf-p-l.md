---
title: "_vscprintf_p —, _vscprintf_p_l —, _vscwprintf_p —, _vscwprintf_p_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vscprintf_p_l
- _vscprintf_p
- _vscwprintf_p_l
- _vscwprintf_p
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
- _vscprintf_p
- _vscprintf_p_l
- vscwprintf_p
- vscprintf_p
- vscwprintf_p_l
- _vscwprintf_p_l
- vscprintf_p_l
- _vscwprintf_p
dev_langs: C++
helpviewer_keywords:
- vscprintf_p function
- _vsctprintf_p_l function
- vscwprintf_p_l function
- _vscwprintf_p_l function
- _vscprintf_p function
- vsctprintf_p function
- _vscprintf_p_l function
- _vscwprintf_p function
- vscwprintf_p function
- vsctprintf_p_l function
- _vsctprintf_p function
- vscprintf_p_l function
ms.assetid: 5da920b3-8652-4ee9-b19e-5aac3ace9d03
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 465260a07a6e18922a67cbb12f3e36b75f60e51a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vscprintfp-vscprintfpl-vscwprintfp-vscwprintfpl"></a>_vscprintf_p, _vscprintf_p_l, _vscwprintf_p, _vscwprintf_p_l
Zwraca liczbę znaków w ciągu sformatowany za pomocą wskaźnika do listy argumentów, z możliwością określić kolejność, w którym są używane argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _vscprintf_p(  
   const char *format,  
   va_list argptr   
);  
int _vscprintf_p _l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vscwprintf_p (  
   const wchar_t *format,  
   va_list argptr   
);  
int _vscwprintf_p _l(  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Ciąg kontroli formatu.  
  
 `argptr`  
 Wskaźnik do listy argumentów.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 `_vscprintf_p`Zwraca liczbę znaków, które może być generowane, jeśli ciąg wskazywał przez listę argumentów została drukowaniu i wysyłane do pliku lub buforu przy użyciu określonego kody formatowania. Wartość zwracana nie zawiera znak końcowy null. `_vscwprintf_p`taką samą funkcję wykonuje dla znaki dwubajtowe.  
  
## <a name="remarks"></a>Uwagi  
 Funkcje te różnią się od `_vscprintf` i `_vscwprintf` tylko w tym obsługują umożliwia określenie kolejności, w którym są używane argumentów. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
 Jeśli `format` wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli może kontynuować wykonywania, funkcje i ustaw `errno` do `EINVAL`.  
  
> [!IMPORTANT]
>  Upewnij się, że jeśli `format` to ciąg zdefiniowany przez użytkownika jest zakończenie wartością null i ma poprawną liczbę i typ parametrów. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vsctprintf_p`|`_vscprintf_p`|`_vscprintf_p`|`_vscwprintf_p`|  
|`_vsctprintf_p_l`|`_vscprintf_p_l`|`_vscprintf_p_l`|`_vscwprintf_p_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_vscprintf_p`, `_vscprintf_p_l`|\<stdio.h >|  
|`_vscwprintf_p`, `_vscwprintf_p_l`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [vsprintf —](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md).  
  
## <a name="see-also"></a>Zobacz też  
 [vprintf — funkcje](../../c-runtime-library/vprintf-functions.md)   
 [_scprintf_p —, _scprintf_p_l —, _scwprintf_p — _scwprintf_p_l —](../../c-runtime-library/reference/scprintf-p-scprintf-p-l-scwprintf-p-scwprintf-p-l.md)   
 [_vscprintf —, _vscprintf_l —, _vscwprintf — _vscwprintf_l —](../../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)