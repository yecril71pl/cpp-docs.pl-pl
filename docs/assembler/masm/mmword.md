---
title: "MMWORD — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0570a55dc11994e12acedb85d3ae8015abefb54c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="mmword"></a>MMWORD
Używany dla argumentów multimedialnych 64-bitowe instrukcje MMX i SSE (XMM).  
  
## <a name="syntax"></a>Składnia  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>Uwagi  
 `MMWORD` jest typem.  Przed mmword — dodawany do MASM równoważne funkcje można zostały osiągnięte z:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Podczas pracy zarówno instrukcje dla operandów 64-bitowych `QWORD` jest typem 64-bitowych liczb całkowitych bez znaku i `MMWORD` jest typem wartości multimedialnych 64-bitowych.  
  
 `MMWORD` reprezentuje ten sam typ co [__m64](../../cpp/m64.md).  
  
## <a name="example"></a>Przykład  
  
```  
movq     mm0, mmword ptr [ebx]  
```