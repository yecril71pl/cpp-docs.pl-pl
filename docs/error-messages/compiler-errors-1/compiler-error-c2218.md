---
title: "Błąd kompilatora C2218 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2218
dev_langs: C++
helpviewer_keywords: C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ca2e431fdfeff3c9dc957bee46f84cfd2c04162
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2218"></a>Błąd kompilatora C2218
"__vectorcall" nie można używać z "/ arch: IA32"  
  
 `__vectorcall` Konwencji wywoływania jest obsługiwana tylko w kodzie natywnym na x86 i x64 procesorów, które obejmują Streaming SIMD Extensions 2 (SSE2) lub nowszym. Aby uzyskać więcej informacji, zobacz [__vectorcall](../../cpp/vectorcall.md).  
  
 Aby naprawić ten błąd, zmień opcje kompilatora na docelowym instrukcji SSE2, AVX i AVX2 ustawia. Aby uzyskać więcej informacji, zobacz [/arch (x86)](../../build/reference/arch-x86.md).