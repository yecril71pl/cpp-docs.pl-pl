---
title: "_ismbbkprint —, _ismbbkprint_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbkprint
- _ismbbkprint_l
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
- _ismbbkprint_l
- ismbbkprint
- _ismbbkprint
- ismbbkprint_l
dev_langs: C++
helpviewer_keywords:
- _ismbbkprint function
- ismbbkprint_l function
- ismbbkprint function
- _ismbbkprint_l function
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9c3f0f105b27c97a0ed775ab18ff3331e7c8627f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ismbbkprint-ismbbkprintl"></a>_ismbbkprint, _ismbbkprint_l
Określa, czy konkretnego znaków wielobajtowych jest symbol interpunkcyjny.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbbkprint(  
   unsigned int c   
);  
int _ismbbkprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Liczba całkowita ma zostać przetestowana.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_ismbbkprint`Zwraca wartość niezerową, jeśli liczba całkowita `c` jest tekst innych niż ASCII lub symbol interpunkcyjny innych niż ASCII lub 0, jeśli nie jest. Na przykład w strona kodowa 932 tylko `_ismbbkprint` testów katakana alfanumeryczne lub znaki interpunkcyjne katakana (zakres: 0xA1 - 0xDF). `_ismbbkprint`używa bieżące ustawienia regionalne dla ustawień zależnych od ustawień regionalnych znaków. `_ismbbkprint_l`jest identyczny z tą różnicą, że używa ustawień regionalnych przekazany. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ismbbkprint`|\<mbctype.h >|  
|`_ismbbkprint_l`|\<mbctype.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)   
 [_ismbb — procedury](../../c-runtime-library/ismbb-routines.md)