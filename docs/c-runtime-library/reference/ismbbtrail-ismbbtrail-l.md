---
title: "_ismbbtrail —, _ismbbtrail_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbtrail
- _ismbbtrail_l
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
- _ismbbtrail
- ismbbtrail
- _ismbbtrail_l
- ismbbtrail_l
dev_langs: C++
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b99e318e95644b327f3629658ac5100f08c05d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ismbbtrail-ismbbtraill"></a>_ismbbtrail, _ismbbtrail_l
Określa, czy bajt końcowego bajtu znaków wielobajtowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbbtrail(  
   unsigned int c   
);  
int _ismbbtrail_l(  
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
 `_ismbbtrail`Zwraca wartość niezerową, jeśli liczba całkowita `c` jest drugi bajt znaków wielobajtowych. Na przykład w kodzie strony 932 tylko, prawidłowe zakresy są 0x40 do 0x7E i 0x80 do 0xFC.  
  
## <a name="remarks"></a>Uwagi  
 `_ismbbtrail`używa bieżące ustawienia regionalne dla zachowania zależnych od ustawień regionalnych. `_ismbbtrail_l`jest identyczny z tą różnicą, że używa ustawień regionalnych, który jest przekazywany w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_ismbbtrail`|\<mbctype.h > lub \<mbstring.h >|\<CType.h >, * \<Limits.h — >, \<stdlib.h >|  
|`_ismbbtrail_l`|\<mbctype.h > lub \<mbstring.h >|\<CType.h >, * \<Limits.h — >, \<stdlib.h >|  
  
 \*Dla manifestu stałe warunki testu.  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)   
 [_ismbb — procedury](../../c-runtime-library/ismbb-routines.md)