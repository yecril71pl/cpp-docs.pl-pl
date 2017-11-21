---
title: "fwide — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fwide
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
apitype: DLLExport
f1_keywords: fwide
dev_langs: C++
helpviewer_keywords: fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f10bd98a6dedba2181aa1d5ebba60f64dda093be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fwide"></a>fwide
Niezaimplementowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fwide(  
   FILE *stream,  
   int mode;  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury (zignorowany).  
  
 `mode`  
 Nową szerokość strumienia: dodatnią dla znaku dwubajtowego ujemny bajt, zero, aby pozostawić bez zmian. (Ta wartość zostanie zignorowana).  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta funkcja jest obecnie tylko zwraca `mode`.  
  
## <a name="remarks"></a>Uwagi  
 Bieżąca wersja ta funkcja nie jest zgodne ze standardem.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fwide`|\<WChar.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).