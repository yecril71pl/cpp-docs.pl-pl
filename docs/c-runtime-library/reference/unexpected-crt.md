---
title: Nieoczekiwany (CRT) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: unexpected
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
f1_keywords: unexpected
dev_langs: C++
helpviewer_keywords: unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 39cc7164a22b95f2c269c7bb1bd558374f56fa3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unexpected-crt"></a>nieoczekiwany (CRT)
Wywołania `terminate` lub można ją określić za pomocą funkcji `set_unexpected`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void unexpected( void );  
```  
  
## <a name="remarks"></a>Uwagi  
 `unexpected` Procedura nie jest używany z bieżąca implementacja C++, obsługa wyjątków. `unexpected`wywołania `terminate` domyślnie. To zachowanie domyślne można zmienić, pisanie funkcji niestandardowych zakończenia i wywołanie `set_unexpected` z nazwą funkcji jako jej argument. `unexpected`wywołuje ostatniej podany jako argument do funkcji `set_unexpected`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`unexpected`|\<EH.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [_set_se_translator —](../../c-runtime-library/reference/set-se-translator.md)   
 [set_terminate —](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set_unexpected —](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [Zakończenie](../../c-runtime-library/reference/terminate-crt.md)