---
title: _CIfmod | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIfmod
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _CIfmod
- CIfmod
dev_langs: C++
helpviewer_keywords:
- CIfmod intrinsic
- _CIfmod intrinsic
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bd1a7f406754f8de985ae5273d7104947a7c7631
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cifmod"></a>_CIfmod
Oblicza resztę zmiennoprzecinkowe górnej wartości na stosie.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __cdecl _CIfmod();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta wersja `fmod` funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany, a ułatwia alokacja rejestru.  
  
 Wartość wynikową spoczywa na wierzchu stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** x86  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmod —, fmodf —](../c-runtime-library/reference/fmod-fmodf.md)