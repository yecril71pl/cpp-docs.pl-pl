---
title: "strcat_s —, wcscat_s —, _mbscat_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strcat_s
- _mbscat_s
- wcscat_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strcat_s
- wcscat_s
- _mbscat_s
dev_langs: C++
helpviewer_keywords:
- wcscat_s function
- strcat_s function
- mbscat_s function
- strings [C++], appending
- _mbscat_s function
- appending strings
ms.assetid: 0f2f9901-c5c5-480b-98bc-f8f690792fc0
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5d508c70ca1a4c44e2b51dfd85b6f85700c111a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="strcats-wcscats-mbscats"></a>strcat_s, wcscat_s, _mbscat_s
Dołącza ciąg. Te wersje programu [strcat —, wcscat —, _mbscat —](../../c-runtime-library/reference/strcat-wcscat-mbscat.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbscat_s`Nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t strcat_s(  
   char *strDestination,  
   size_t numberOfElements,  
   const char *strSource   
);  
errno_t wcscat_s(  
   wchar_t *strDestination,  
   size_t numberOfElements,  
   const wchar_t *strSource   
);  
errno_t _mbscat_s(  
   unsigned char *strDestination,  
   size_t numberOfElements,  
   const unsigned char *strSource   
);  
template <size_t size>  
errno_t strcat_s(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
errno_t wcscat_s(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
errno_t _mbscat_s(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDestination`  
 Bufor ciąg docelowy zerem.  
  
 `numberOfElements`  
 Rozmiar buforu ciągu docelowego.  
  
 `strSource`  
 Bufor ciąg źródłowy zerem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; błąd o kodzie błędu.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`strDestination`|`numberOfElements`|`strSource`|Wartość zwracana|Zawartość`strDestination`|  
|----------------------|------------------------|-----------------|------------------|----------------------------------|  
|`NULL`lub niezakończony|wszystkie|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|wszystkie|wszystkie|`NULL`|`EINVAL`|`strDestination`zestawu [0] 0|  
|wszystkie|0 lub za mały|wszystkie|`ERANGE`|`strDestination`zestawu [0] 0|  
  
## <a name="remarks"></a>Uwagi  
 `strcat_s` Funkcja dołącza `strSource` do `strDestination` i kończy wynikowy ciąg ze znakiem null. Litery `strSource` zastępuje znak końcowy null z `strDestination`. Zachowanie `strcat_s` zdefiniowano nakładania się ciągów źródłowych i docelowych.  
  
 Należy pamiętać, że drugi parametr całkowity rozmiar buforu nie pozostały rozmiar:  
  
```  
char buf[16];  
strcpy_s(buf, 16, "Start");  
strcat_s(buf, 16, " End");               // Correct  
strcat_s(buf, 16 - strlen(buf), " End"); // Incorrect  
```  
  
 `wcscat_s`i `_mbscat_s` znaków dwubajtowych i znaków wielobajtowych wersji `strcat_s`. Argumenty i zwracana wartość `wcscat_s` są znaków dwubajtowych ciągi; tych `_mbscat_s` są ciągami znaków wielobajtowych. Te trzy funkcje działają tak samo w przeciwnym razie wartość.  
  
 Jeśli `strDestination` jest wskaźnika o wartości null lub nie jest zerem, lub jeśli `strSource` jest `NULL` wskaźnika, lub czy ciągu docelowego jest za mały, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `EINVAL` i ustaw `errno` do `EINVAL`.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Wersje tych funkcji do debugowania najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscat_s`|`strcat_s`|`_mbscat_s`|`wcscat_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strcat_s`|\<String.h >|  
|`wcscat_s`|\<String.h > lub \<wchar.h >|  
|`_mbscat_s`|\<mbstring.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem kodu w [strcpy_s —, wcscpy_s —, _mbscpy_s —](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [strncat —, _strncat_l, wcsncat —, _wcsncat_l _mbsncat —, _mbsncat_l —](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy —, _strncpy_l —, wcsncpy —, _wcsncpy_l — _mbsncpy —, _mbsncpy_l —](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [_strnicmp —, _wcsnicmp —, _mbsnicmp —, _strnicmp_l — _wcsnicmp_l —, _mbsnicmp_l —](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr —, wcsrchr —, _mbsrchr — _mbsrchr_l —](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn —, wcsspn —, _mbsspn — _mbsspn_l —](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)