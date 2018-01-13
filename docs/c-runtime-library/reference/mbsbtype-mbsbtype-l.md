---
title: "_mbsbtype —, _mbsbtype_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs: C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 05c106136c36d09b06e5b168a0c582b87c306d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l
Zwraca typ bajtów ciągu.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _mbsbtype(  
   const unsigned char *mbstr,  
   size_t count   
);  
int _mbsbtype_l(  
   const unsigned char *mbstr,  
   size_t count,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mbstr`  
 Adres sekwencji znaków wielobajtowych.  
  
 `count`  
 Przesunięcie bajtów, z węzła głównego w ciągu.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_mbsbtype`i `_mbsbtype_l` zwraca wartość wskazująca wynik testu w określonym bajcie. Stałe manifestu w poniższej tabeli są definiowane w Mbctype.h.  
  
|Wartość zwracana|Byte — typ|  
|------------------|---------------|  
|`_MBC_SINGLE` (0)|Znaki jednobajtowe. Na przykład w strona kodowa 932 `_mbsbtype` zwraca wartość 0, jeśli w określonym bajcie znajduje się w zakresie wartości 0x20-0x7E lub 0xA1 - 0xDF.|  
|`_MBC_LEAD` (1)|Prowadzić bajtów znaków wielobajtowych. Na przykład w strona kodowa 932 `_mbsbtype` zwraca wartość 1, jeśli w określonym bajcie znajduje się w zakresie 0x81-0x9F lub wartość 0xE0 - 0xFC.|  
|`_MBC_TRAIL` (2)|Końcowy bajtów znaków wielobajtowych. Na przykład w strona kodowa 932 `_mbsbtype` zwraca 2, jeśli w określonym bajcie znajduje się w zakresie 0x40-0x7E lub 0x80 - 0xFC.|  
|`_MBC_ILLEGAL` (-1)|`NULL`ciąg, nieprawidłowy znak lub `NULL` bajtów znaleziono przed bajtów przy przesunięciu `count` w `mbstr`.|  
  
## <a name="remarks"></a>Uwagi  
 `_mbsbtype` Funkcja określa typ bajtów w ciąg znaków wielobajtowych. Funkcja sprawdza, czy tylko bajtów przy przesunięciu `count` w `mbstr`, ignorowanie nieprawidłowe znaki, przed określonym bajcie.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersja tej funkcji bez `_l` sufiks używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersja z `_l` sufiks jest identyczny z tą różnicą, że on używać zamiast niej przekazany parametr ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Jeśli ciąg wejściowy jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `_MBC_ILLEGAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_mbsbtype`|\<mbstring.h >|\<mbctype.h > *|  
|`_mbsbtype_l`|\<mbstring.h >|\<mbctype.h > *|  
  
 \*Dla manifest stałe używane jako wartości zwracanych.  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)