---
title: "srand — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: srand
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords: srand
dev_langs: C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 99847da3be2e311ac9cb0da301ed4729705ad9fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="srand"></a>srand
Ustawia wartość początkową inicjatora dla generatora liczb pseudolosowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `seed`  
 Inicjator dla Generowanie liczb pseudolosowych  
  
## <a name="remarks"></a>Uwagi  
 `srand` Funkcja określa punkt początkowy generowania serii liczb pseudolosowych w bieżącym wątku. Aby ponownie zainicjować generatora, aby utworzyć taką samą sekwencję wyników, należy wywołać `srand` funkcji i używać tego samego `seed` argument ponownie. Wszystkie inne wartości `seed` ustawia generator do innego punktu początkowego pseudolosowych sekwencji. `rand`pobiera liczb pseudolosowych, które zostały wygenerowane. Wywoływanie `rand` przed wywołaniem dowolnej `srand` generuje takiej samej kolejności, co wywołanie `srand` z `seed` przekazany jako 1.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`srand`|\<stdlib.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [rand](../../c-runtime-library/reference/rand.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [RAND](../../c-runtime-library/reference/rand.md)