---
title: C3715 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9412592ac177fb49f065975db469c9f77b98e8c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3715"></a>C3715 błąd kompilatora
"wskaźnik": musi być wskaźnikiem do "class"  
  
 Określony wskaźnika w [__hook](../../cpp/hook.md) lub [__unhook](../../cpp/unhook.md) nie wskazywały który prawidłową klasę. Aby naprawić ten błąd, upewnij się, że Twoje `__hook` i `__unhook` wywołania Określ wskaźniki do prawidłowych klas.