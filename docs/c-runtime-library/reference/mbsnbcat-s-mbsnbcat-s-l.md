---
title: "_mbsnbcat_s —, _mbsnbcat_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
apitype: DLLExport
f1_keywords:
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
dev_langs:
- C++
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb76afdd5c6e85b8c3101678ddd27351f2aa0c1b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s, _mbsnbcat_s_l
Dołącza co najwyżej na ciąg znaków wielobajtowych pierwszy `n` bajtów inny ciąg znaków wielobajtowych. Są to wersje [_mbsnbcat —, _mbsnbcat_l —](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md) ulepszenia zabezpieczeń, które mają zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _mbsnbcat_s(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count   
);  
errno_t _mbsnbcat_s_l(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbcat_s(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbcat_s_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Ciąg docelowego znaków wielobajtowych zerem.  
  
 `sizeInBytes`  
 Rozmiar `dest` buforu w bajtach.  
  
 `src`  
 Ciąg źródłowy znaków wielobajtowych zerem.  
  
 `Count`  
 Liczba bajtów z `src` do dołączenia do `dest`.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`Dest`|`sizeInBytes`|`src`|Wartość zwracana|  
|------------|-------------------|-----------|------------------|  
|`NULL`|wszystkie|wszystkie|`EINVAL`|  
|wszystkie|<= 0|wszystkie|`EINVAL`|  
|wszystkie|wszystkie|`NULL`|`EINVAL`|  
  
 Jeśli wystąpi błąd warunki, funkcja generuje błąd nieprawidłowego parametru zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli ten błąd jest obsługiwane, funkcja zwraca `EINVAL` i ustawia `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_mbsnbcat_s` Funkcja dołącza do `dest`, co najwyżej pierwszy `count` bajtów `src`. Jeśli bajtów to bezpośrednio przed znakiem pustym w `dest` jest bajtu, jest on zastąpiony przez początkowej bajt `src`. W przeciwnym razie wartość początkowa bajt `src` zastępuje znak końcowy null z `dest`. Jeśli null bajt jest wyświetlany w `src` przed `count` bajtów są dołączane, `_mbsnbcat_s` dołącza wszystkich bajtów z `src`, maksymalnie znakiem pustym. Jeśli `count` jest większa niż długość `src`, długość `src` jest używany zamiast `count`. Wynikowy ciąg kończy się znakiem null. Jeśli kopiowanie odbywa się między ciągów, które nakładają się na, zachowanie jest niezdefiniowany.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje te funkcje są identyczne, z tą różnicą, że te nie mają `_l` używać sufiksu bieżące ustawienia regionalne i te, które `_l` sufiks zamiast tego użyć parametr ustawień regionalnych, który jest przekazywany w. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 W języku C++ użycia tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie co eliminuje konieczność określić argument rozmiar i mogą automatycznie przy użyciu ich funkcji nowsze, bardziej bezpieczne zastąpienie starszych funkcji o niższym poziomie zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Wersje tych funkcji do debugowania najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsncat`|[strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat_s`|[wcsncat —](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_s_l`|`_strncat_s_l`|`_mbsnbcat_s_l`|`_wcsncat_s_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbsnbcat_s`|\<mbstring.h>|  
|`_mbsnbcat_s_l`|\<mbstring.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcmp —, _mbsnbcmp_l —](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [_mbsnbcpy, _mbsnbcpy_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [_mbsnbcpy_s, _mbsnbcpy_s_l](../../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)   
 [_mbsnbset —, _mbsnbset_l —](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat —, _strncat_l, wcsncat —, _wcsncat_l _mbsncat —, _mbsncat_l —](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)