---
title: "C3715 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca60dcff0279982b01c70ee3c7603baf421bd434
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3715"></a>C3715 błąd kompilatora
"wskaźnik": musi być wskaźnikiem do "class"  
  
 Określony wskaźnika w [__hook](../../cpp/hook.md) lub [__unhook](../../cpp/unhook.md) nie wskazywały który prawidłową klasę. Aby naprawić ten błąd, upewnij się, że Twoje `__hook` i `__unhook` wywołania Określ wskaźniki do prawidłowych klas.