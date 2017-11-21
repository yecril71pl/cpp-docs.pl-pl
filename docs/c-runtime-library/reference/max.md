---
title: "__max — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __max
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
f1_keywords:
- max
- __max
dev_langs: C++
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63c45f6466b6a47d92b5dd82d5d5b43fb09d94d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="max"></a>__max
Zwraca większy z dwóch wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
type __max(  
   type a,  
   type b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Wszystkie dane typu liczbowego.  
  
 `a, b`  
 Wartości typu liczbowego do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `__max`Zwraca większy z jego argumentów.  
  
## <a name="remarks"></a>Uwagi  
 `__max` Makro porównuje dwie wartości i zwraca wartość typu, który większy. Argumenty mogą być dowolnego liczbowego typu danych, podpisu lub bez znaku. Zarówno argumentów i zwracana wartość musi być tego samego typu danych.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`__max`|\<stdlib.h >|  
  
## <a name="example"></a>Przykład  
 Aby uzyskać więcej informacji, zobacz przykład [__min —](../../c-runtime-library/reference/min.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [__min —](../../c-runtime-library/reference/min.md)