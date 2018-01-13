---
title: "MMWORD — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MMWORD
dev_langs: C++
helpviewer_keywords: MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbe20f842a97186071431cd73e7de65fa8170bd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mmword"></a>MMWORD
Używany dla argumentów multimedialnych 64-bitowe instrukcje MMX i SSE (XMM).  
  
## <a name="syntax"></a>Składnia  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>Uwagi  
 `MMWORD`jest typem.  Przed mmword — dodawany do MASM równoważne funkcje można zostały osiągnięte z:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Podczas pracy zarówno instrukcje dla operandów 64-bitowych `QWORD` jest typem 64-bitowych liczb całkowitych bez znaku i `MMWORD` jest typem wartości multimedialnych 64-bitowych.  
  
 `MMWORD`reprezentuje ten sam typ co [__m64](../../cpp/m64.md).  
  
## <a name="example"></a>Przykład  
  
```  
movq     mm0, mmword ptr [ebx]  
```