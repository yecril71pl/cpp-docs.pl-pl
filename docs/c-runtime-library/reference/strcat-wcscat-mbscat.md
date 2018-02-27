---
title: "strcat —, wcscat —, _mbscat — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mbscat
- wcscat
- strcat
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
- _mbscat
- _ftcscat
- _tcscat
- strcat
- wcscat
dev_langs:
- C++
helpviewer_keywords:
- concatenating strings
- mbscat function
- _ftcscat function
- _tcscat function
- ftcscat function
- strcat function
- strings [C++], appending
- _mbscat function
- tcscat function
- strings [C++], concatenating
- appending strings
- wcscat function
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd2abb7326735cb84ffc8905d1ed30e030c88559
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="strcat-wcscat-mbscat"></a>strcat, wcscat, _mbscat
Dołącza ciąg. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [strcat_s —, wcscat_s —, _mbscat_s —](../../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md).  
  
> [!IMPORTANT]
>  `_mbscat_s` Nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *strcat(  
   char *strDestination,  
   const char *strSource   
);  
wchar_t *wcscat(  
   wchar_t *strDestination,  
   const wchar_t *strSource   
);  
unsigned char *_mbscat(  
   unsigned char *strDestination,  
   const unsigned char *strSource   
);  
template <size_t size>  
char *strcat(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
wchar_t *wcscat(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
unsigned char *_mbscat(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDestination`  
 Ciąg docelowego zerem.  
  
 `strSource`  
 Ciąg źródłowy zerem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca ciąg docelowego (`strDestination`). Brak wartości zwracanej jest zarezerwowana wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 `strcat` Funkcja dołącza `strSource` do `strDestination` i kończy wynikowy ciąg ze znakiem null. Litery `strSource` zastępuje znak końcowy null z `strDestination`. Zachowanie `strcat` zdefiniowano nakładania się ciągów źródłowych i docelowych.  
  
> [!IMPORTANT]
>  Ponieważ `strcat` nie sprawdza wystarczającą ilość miejsca w `strDestination` przed dołączeniem `strSource`, jest przyczyną przepełnienia buforu. Należy rozważyć użycie [strncat —](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) zamiast tego.  
  
 `wcscat` i `_mbscat` znaków dwubajtowych i znaków wielobajtowych wersji `strcat`. Argumenty i zwracana wartość `wcscat` są znaków dwubajtowych ciągi; tych `_mbscat` są ciągami znaków wielobajtowych. Te trzy funkcje działają tak samo w przeciwnym razie wartość.  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscat`|`strcat`|`_mbscat`|`wcscat`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strcat`|\<string.h>|  
|`wcscat`|\<String.h > lub \<wchar.h >|  
|`_mbscat`|\<mbstring.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [strncat —, _strncat_l, wcsncat —, _wcsncat_l _mbsncat —, _mbsncat_l —](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr —, wcsrchr —, _mbsrchr — _mbsrchr_l —](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)