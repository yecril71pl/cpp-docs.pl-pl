---
title: "_ismbbgraph —, _ismbbgraph_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbgraph_l
- _ismbbgraph
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
- _ismbbgraph
- _ismbbgraph_l
- ismbbgraph
- ismbbgraph_l
dev_langs: C++
helpviewer_keywords:
- _ismbbgraph_l function
- ismbbgraph_l function
- _ismbbgraph function
- ismbbgraph function
ms.assetid: b60db718-134f-4796-acc1-592d0b9efbb7
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d0f4ac9be945802b596505f723b1a9da00356d8e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ismbbgraph-ismbbgraphl"></a>_ismbbgraph, _ismbbgraph_l
Określa, czy konkretnego znaków wielobajtowych jest znak graficzny.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbbgraph (  
   unsigned int c   
);  
int _ismbbgraph_l (  
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
 Zwraca wartość niezerową, jeśli wyrażenie:  
  
```  
( _PUNCT | _UPPER | _LOWER | _DIGIT ) || _ismbbkprint  
```  
  
 jest różna od zera dla `c`, lub wartość 0, jeśli nie jest. `_ismbbgraph`używa bieżące ustawienia regionalne dla dowolnego zachowanie zależnych od ustawień regionalnych. `_ismbbgraph_l`jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ismbbgraph`|\<mbctype.h >|  
|`_ismbbgraph_l`|\<mbctype.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)   
 [_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)