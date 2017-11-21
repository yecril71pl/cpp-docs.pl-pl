---
title: "_ismbbalnum —, _ismbbalnum_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbalnum
- _ismbbalnum_l
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
- _ismbbalnum
- ismbbalnum
- _ismbbalnum_l
- ismbbalnum_l
dev_langs: C++
helpviewer_keywords:
- _ismbbalnum_l function
- ismbbalnum function
- ismbbalnum_l function
- _ismbbalnum function
ms.assetid: 8025de50-a871-49fd-9ae6-f437b47aa987
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebfeefa7a0a0e5f065ad397e71dfcbc26012aa65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ismbbalnum-ismbbalnuml"></a>_ismbbalnum, _ismbbalnum_l
Określa, czy określony znaków wielobajtowych jest alfa lub liczbowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbbalnum(  
   unsigned int c   
);  
int _ismbbalnum_l(  
   unsigned int c   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Liczba całkowita ma zostać przetestowana.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_ismbbalnum`Zwraca wartość niezerową, jeśli wyrażenie:  
  
```  
isalnum || _ismbbkalnum  
```  
  
 jest różna od zera dla `c`, lub wartość 0, jeśli nie jest.  
  
 Wersja tej funkcji z `_l` sufiks jest identyczny z tą różnicą, że używa ustawień regionalnych przekazana zamiast bieżące ustawienia regionalne dla jego działania zależnego od ustawień regionalnych.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ismbbalnum`|\<mbctype.h >|  
|`_ismbbalnum_l`|\<mbctype.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)   
 [_ismbb — procedury](../../c-runtime-library/ismbb-routines.md)