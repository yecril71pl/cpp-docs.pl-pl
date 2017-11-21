---
title: "_mbccpy —, _mbccpy_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbccpy
- _mbccpy_l
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
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
dev_langs: C++
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 11f5a9a0629aa7012418cdb74d849d838e8cc5b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l
Kopiuje znaków wielobajtowych z jednego ciągu na inny ciąg. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_mbccpy_s —, _mbccpy_s_l —](../../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _mbccpy(  
   unsigned char *dest,  
   const unsigned char *src   
);  
void _mbccpy_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Lokalizacji docelowej kopiowania.  
  
 `src`  
 Znaków wielobajtowych do skopiowania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="remarks"></a>Uwagi  
 `_mbccpy` Funkcja kopiuje znaków wielobajtowych jednego z `src` do `dest`.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `_mbccpy` jest przekazywany wskaźnika o wartości null `dest` lub `src`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ma ustawioną wartość `EINVAL`.  
  
 `_mbccpy`używa bieżące ustawienia regionalne dla dowolnego zachowanie zależnych od ustawień regionalnych. `_mbccpy_l`jest taka sama jak `_mbccpy` z tą różnicą, że `_mbccpy_l` korzysta z ustawień regionalnych przekazano wszystkie działania zależne od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 **Uwaga dotycząca zabezpieczeń** użyć ciągu zakończonego wartością null. Ciąg znaków zakończony znakiem null nie może przekraczać rozmiar buforu docelowego. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795). Przepełnienie buforu problemy używanej metody ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tccpy`|Map — makro lub wewnętrznej funkcji|`_mbccpy`|Map — makro lub wewnętrznej funkcji|  
|`_tccpy_l`|n/d|`_mbccpy_l`|n/d|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbccpy`|\<mbctype.h >|  
|`_mbccpy_l`|\<mbctype.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen —, mblen —, _mblen_l —](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)