---
title: "isleadbyte —, _isleadbyte_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isleadbyte_l
- isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
dev_langs: C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6d679d634d14f3a762a6ef3d32d2ca4c5d4b6f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l
Określa, czy znak jest bajtu znaków wielobajtowych.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int isleadbyte(  
   int c   
);  
int _isleadbyte_l(  
   int c   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Liczba całkowita do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `isleadbyte`Zwraca wartość niezerową, jeśli argument spełnia warunek testu lub 0, jeśli jej nie ma. Zgodnie z ustawieniami regionalnymi "C" i jednobajtowych (SBCS), ustawienia regionalne, zestaw znaków `isleadbyte` zawsze zwraca wartość 0.  
  
## <a name="remarks"></a>Uwagi  
 `isleadbyte` Makro zwraca wartość niezerową, jeśli jej argument pierwszy bajt znaków wielobajtowych. `isleadbyte`zapewnia łatwy do rozpoznania wynik argumentu liczba całkowita od -1 (`EOF`) do `UCHAR_MAX` (0xFF) włącznie.  
  
 Oczekiwano argumentu rodzaju `isleadbyte` jest `int`; Jeśli podpisem znak zostanie przekazany, kompilator może ją przekonwertować na liczbę całkowitą przez rozszerzenie logowania, którego można nieprzewidywalne skutki.  
  
 Wersja tej funkcji z `_l` sufiks jest identyczny z tą różnicą, że używa ustawień regionalnych przekazana zamiast bieżące ustawienia regionalne dla jego działania zależnego od ustawień regionalnych.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istleadbyte`|Zawsze zwraca wartość false|**_** `isleadbyte`|Zawsze zwraca wartość false|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`isleadbyte`|\<CType.h >|  
|`_isleadbyte_l`|\<CType.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [_ismbb — procedury](../../c-runtime-library/ismbb-routines.md)