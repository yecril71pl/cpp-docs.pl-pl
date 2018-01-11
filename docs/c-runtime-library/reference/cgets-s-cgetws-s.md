---
title: "_cgets_s —, _cgetws_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
dev_langs: C++
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28e35d5f2eb2f07cd1b02fa8b1edc3f41b2c2174
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cgetss-cgetwss"></a>_cgets_s, _cgetws_s
Pobiera ciąg znaków z konsoli. Te wersje programu [_cgets — i _cgetws —](../../c-runtime-library/cgets-cgetws.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _cgets_s(   
   char *buffer,  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
errno_t _cgetws_s(  
   wchar_t *buffer  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
template <size_t size>  
errno_t _cgets_s(   
   char (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
template <size_t size>  
errno_t _cgetws_s(  
   wchar_t (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Lokalizacja magazynu danych.  
  
 [in]`numberOfElements`  
 Rozmiar buforu w znaki jednobajtowe lub szerokie, która jest również maksymalną liczbę znaków do odczytania.  
  
 [in]`pSizeRead`  
 Liczba znaków faktycznie odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest wartość zero w przypadku powodzenia; w przeciwnym razie kod błędu, jeśli wystąpi błąd.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`buffer`|`numberOfElements`|`pSizeRead`|Zwraca|Zawartość`buffer`|  
|--------------|------------------------|-----------------|------------|--------------------------|  
|`NULL`|wszystkie|wszystkie|`EINVAL`|n/d|  
|nie`NULL`|zero|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|nie`NULL`|wszystkie|`NULL`|`EINVAL`|Ciąg o zerowej długości|  
  
## <a name="remarks"></a>Uwagi  
 `_cgets_s`i `_cgetws_s` odczytać ciągu z konsoli i skopiuj ciąg (z terminatorem null) do `buffer`. `_cgetws_s`jest to wersja znaków dwubajtowych w funkcji; inne niż rozmiar znaków zachowanie tych dwóch funkcji jest identyczne. Maksymalny rozmiar ciągu do odczytu jest przekazywany jako `numberOfElements` parametru. Ten rozmiar powinna zawierać nadmiarowe znaki do zakończenia wartości null. Rzeczywista liczba znaków do odczytu jest umieszczany w `pSizeRead`.  
  
 Jeśli wystąpi błąd podczas operacji lub podczas sprawdzania poprawności parametrów, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i `EINVAL` jest zwracany.  
  
 W języku C++ użycia tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, a tym samym wyeliminowanie konieczności określania argumentem rozmiaru i automatycznie można zastąpić starszą funkcji o niższym poziomie zabezpieczeń z ich odpowiedniki nowsze, bardziej bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts_s`|`_cgets_s`|`_cgets_s`|`_cgetws_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_cgets_s`|\<conio.h >|  
|`_cgetws_s`|\<conio.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_getch, _getwch](../../c-runtime-library/reference/getch-getwch.md)