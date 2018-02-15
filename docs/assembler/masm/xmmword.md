---
title: "XMMWORD — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- XMMWORD
dev_langs:
- C++
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6844ab0d83fec2ed78a72238c510906aa7ecc8d9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="xmmword"></a>XMMWORD
Używany dla argumentów multimedialnych 128-bitowe instrukcje MMX i SSE (XMM).  
  
## <a name="syntax"></a>Składnia  
  
```  
XMMWORD  
```  
  
## <a name="remarks"></a>Uwagi  
 `XMMWORD` reprezentuje ten sam typ co [__m128](../../cpp/m128.md).  
  
## <a name="example"></a>Przykład  
  
```  
movdqa   xmm0, xmmword ptr [ebx]  
```