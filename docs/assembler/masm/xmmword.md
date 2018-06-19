---
title: XMMWORD — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- XMMWORD
dev_langs:
- C++
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8fd8e6c82a3275161e519eeead490473e8d64ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056421"
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