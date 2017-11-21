---
title: "_ismbbprint —, _ismbbprint_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbprint_l
- _ismbbprint
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
- _ismbbprint_l
- _ismbbprint
- ismbbprint
- ismbbprint_l
dev_langs: C++
helpviewer_keywords:
- ismbbprint_l function
- ismbbprint function
- _ismbbprint function
- _ismbbprint_l function
ms.assetid: d08a061c-18a8-48f2-a75d-bff4870aec9d
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 451128fda38e5733cc9650e4783964d8c8aebfdc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ismbbprint-ismbbprintl"></a>_ismbbprint, _ismbbprint_l
Określa, czy określony znaków wielobajtowych jest znak wydruku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbbprint(  
   unsigned int c   
);  
int _ismbbprint_l(  
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
 `_ismbbprint`Zwraca wartość niezerową, jeśli wyrażenie:  
  
```  
isprint || _ismbbkprint  
```  
  
 jest różna od zera dla `c`, lub wartość 0, jeśli nie jest. `_ismbbprint`używa bieżące ustawienia regionalne dla dowolnego zachowanie zależnych od ustawień regionalnych. `_ismbbprint_l`jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ismbbprint`|\<mbctype.h >|  
|`_ismbbprint_l`|\<mbctype.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)   
 [_ismbb — procedury](../../c-runtime-library/ismbb-routines.md)