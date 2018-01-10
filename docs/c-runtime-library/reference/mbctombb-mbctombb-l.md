---
title: "_mbctombb —, _mbctombb_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
dev_langs: C++
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 327c55d92b9d23644807ecd52dbecf0fd0b62375
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbctombb-mbctombbl"></a>_mbctombb, _mbctombb_l
Konwertuje odpowiednich znaków wielobajtowych jednobajtowe znaków wielobajtowych znaków dwubajtowych.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned int _mbctombb(  
   unsigned int c   
);  
unsigned int _mbctombb_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znaków wielobajtowych do konwersji.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `_mbctombb` i `_mbctombb_l` zwraca znaki jednobajtowe odpowiada `c`; w przeciwnym razie zwraca `c`.  
  
## <a name="remarks"></a>Uwagi  
 `_mbctombb` i `_mbctombb_l` funkcji konwertuje dany znaków wielobajtowych do odpowiednich znaków wielobajtowych jednobajtowe. Znaki muszą odpowiadać znaki jednobajtowe w zakresie wartości 0x20-0x7E lub 0xA1 - 0xDF do skonwertowania.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersja tej funkcji bez `_l` sufiks używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersja z `_l` sufiks jest identyczny z tą różnicą, że on używać zamiast niej przekazany parametr ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 W poprzednich wersjach `_mbctombb` wywołano `zentohan`. Zamiast nich należy używać słów kluczowych `_mbctombb`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbctombb`|\<mbstring.h >|  
|`_mbctombb_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [_mbbtombc —, _mbbtombc_l —](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbcjistojms —, _mbcjistojms_l —, _mbcjmstojis — _mbcjmstojis_l —](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [_mbctohira —, _mbctohira_l —, _mbctokata — _mbctokata_l —](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)