---
title: "_mbctohira —, _mbctohira_l —, _mbctokata —, _mbctokata_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
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
- _mbctokata
- mbctohira
- _mbctohira
- _mbctohira_l
- mbctokata
- mbctokata_l
- mbctohira_l
- _mbctokata_l
dev_langs: C++
helpviewer_keywords:
- _mbctokata function
- _mbctokata_l function
- _mbctohira_l function
- mbctohira_l function
- mbctohira function
- mbctokata_l function
- _mbctohira function
- mbctokata function
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a398e2d0b55a8c3292a77ba957982fa5a5e21f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mbctohira-mbctohiral-mbctokata-mbctokatal"></a>_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
Wykonuje konwersję między znakami hiragana i katakana.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned int _mbctohira(  
   unsigned int c   
);  
unsigned int _mbctohira_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbctokata(  
   unsigned int c   
);  
unsigned int _mbctokata_l(  
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
 Każda z tych funkcji zwraca znak przekonwertowany `c`, jeśli to możliwe. W przeciwnym razie zwraca znak `c` bez zmian.  
  
## <a name="remarks"></a>Uwagi  
 `_mbctohira` i `_mbctokata` funkcji testowania znak `c` i, jeśli to możliwe, zastosuj jedną z następujących konwersji.  
  
|Procedury|Konwertuje|  
|--------------|--------------|  
|`_mbctohira,_mbctohira_l`|Katakana wielobajtowe do wielobajtowe hiragana.|  
|`_mbctokata,_mbctokata_l`|Wielobajtowe hiragana na katakana wielobajtowe.|  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje te funkcje są identyczne, z tą różnicą, że te nie mają `_l` sufiks na użytek bieżące ustawienia regionalne to zachowanie zależnych od ustawień regionalnych i te, które `_l` sufiks zamiast tego użyj parametru ustawienia regionalne to jest Przekazano. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 We wcześniejszych wersjach `_mbctohira` miał nazwę `jtohira` i `_mbctokata` miał nazwę `jtokata`. Nowy kod można użyć nowej nazwy.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbctohira`|\<mbstring.h >|  
|`_mbctohira_l`|\<mbstring.h >|  
|`_mbctokata`|\<mbstring.h >|  
|`_mbctokata_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [_mbcjistojms —, _mbcjistojms_l —, _mbcjmstojis — _mbcjmstojis_l —](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [_mbctolower —, _mbctolower_l —, _mbctoupper — _mbctoupper_l —](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)   
 [_mbctombb —, _mbctombb_l —](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)