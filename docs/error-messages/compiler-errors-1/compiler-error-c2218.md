---
title: Błąd kompilatora C2218 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1efda7258616862efc464b493b51ada2c6bd7674
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172214"
---
# <a name="compiler-error-c2218"></a>Błąd kompilatora C2218
"__vectorcall" nie można używać z "/ arch: IA32"  
  
 `__vectorcall` Konwencji wywoływania jest obsługiwana tylko w kodzie natywnym na x86 i x64 procesorów, które obejmują Streaming SIMD Extensions 2 (SSE2) lub nowszym. Aby uzyskać więcej informacji, zobacz [__vectorcall](../../cpp/vectorcall.md).  
  
 Aby naprawić ten błąd, zmień opcje kompilatora na docelowym instrukcji SSE2, AVX i AVX2 ustawia. Aby uzyskać więcej informacji, zobacz [/arch (x86)](../../build/reference/arch-x86.md).