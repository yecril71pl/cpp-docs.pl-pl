---
title: "_strdate_s —, _wstrdate_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strdate_s
- _wstrdate_s
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
dev_langs: C++
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71117aed66d83c2c2ae1651c4de9c91e06a43653
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="strdates-wstrdates"></a>_strdate_s, _wstrdate_s
Skopiuj bieżącą datę systemową w buforze. Są to wersje [_strdate —, _wstrdate —](../../c-runtime-library/reference/strdate-wstrdate.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _strdate_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrdate_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strdate_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrdate_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Wskaźnik do buforu, który zostanie wprowadzona wartość ciągu daty sformatowane.  
  
 [in]`numberOfElements`  
 Rozmiar buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu w przypadku awarii. Kody błędów są definiowane w numer błędu. H; Zobacz tabelę poniżej, aby dokładnie błędy generowane przez tę funkcję. Aby uzyskać więcej informacji o kodach błędów, zobacz [errno](../../c-runtime-library/errno-constants.md).  
  
## <a name="error-conditions"></a>Warunki błędów  
  
|`buffer`|`numberOfElements`|Zwraca|Zawartość`buffer`|  
|--------------|------------------------|------------|--------------------------|  
|`NULL`|(wszystkie)|`EINVAL`|Nie zmodyfikowano|  
|Nie `NULL` (prawidłowego buforu wskazująca)|0|`EINVAL`|Nie zmodyfikowano|  
|Nie `NULL` (prawidłowego buforu wskazująca)|0 < `numberOfElements` < 9|`EINVAL`|Pusty ciąg|  
|Nie `NULL` (prawidłowego buforu wskazująca)|`numberOfElements` >= 9|0|Bieżącą datę w formacie określonym w uwagi|  
  
## <a name="security-issues"></a>Problemy z zabezpieczeniami  
 Przekazywanie nieprawidłowe z systemem innym niż `NULL` wartość dla buforu spowoduje naruszenie zasad dostępu Jeśli `numberOfElements` parametru jest większa niż 9.  
  
 Przekazywanie wartości dla rozmiaru, który jest większy niż rzeczywisty rozmiar `buffer` spowoduje przepełnienie buforu.  
  
## <a name="remarks"></a>Uwagi  
 Funkcje te zapewniają bardziej bezpieczne wersje `_strdate` i `_wstrdate`. `_strdate_s` Funkcja kopiuje bieżącej systemowej daty do bufor wskazywany przez `buffer`, sformatowany `mm` / `dd` / `yy`, gdzie `mm` jest reprezentujący dwie cyfry miesiąc, `dd` to dwie cyfry reprezentującą dzień, a `yy` to dwa ostatnie cyfry roku. Na przykład ciąg `12/05/99` reprezentuje 5 grudnia 1999. Rozmiar buforu musi być co najmniej 9 znaków.  
  
 `_wstrdate_s`jest to wersja znaków dwubajtowych `_strdate_s`; argumentów i wartości `_wstrdate_s` są ciągami znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.  
  
 Jeśli `buffer` jest `NULL` wskaźnika, lub jeśli `numberOfElements` jest mniejsza niż 9 znaków, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw `errno` do `EINVAL` Jeśli bufor jest `NULL` lub, jeśli `numberOfElements` jest mniejsza niż lub równa 0 lub zestawu `errno` do `ERANGE` Jeśli `numberOfElements` jest mniejsza niż 9.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mapping"></a>Rutynowe mapowanie — zwykły tekst:  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrdate_s`|`_strdate_s`|`_strdate_s`|`_wstrdate_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_strdate`|\<Time.h >|  
|`_wstrdate`|\<Time.h > lub \<wchar.h >|  
|`_strdate_s`|\<Time.h >|  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [czas](../../c-runtime-library/reference/time-time32-time64.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime_s —, _wasctime_s —](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime_s —, _ctime32_s —, _ctime64_s —, _wctime_s — _wctime32_s —, _wctime64_s —](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime_s —, _gmtime32_s —, _gmtime64_s —](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime —, _mktime32 —, _mktime64 —](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [czas, _time32 —, _time64 —](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)