---
title: C3198 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3198
dev_langs:
- C++
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0516e7cae12e544195d157781e6ed86923470420
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250908"
---
# <a name="compiler-error-c3198"></a>C3198 błąd kompilatora
Nieprawidłowe użycie zmiennoprzecinkowych pragm: fenv_access pragma działa tylko w trybie ścisłym  
  
 [fenv_access](../../preprocessor/fenv-access.md) pragma została użyta w obszarze [/FP](../../build/reference/fp-specify-floating-point-behavior.md) inne niż ustawienie **/FP: precise**.  
  
 Poniższy przykład generuje C3198:  
  
```  
// C3198.cpp  
// compile with: /fp:fast  
#pragma fenv_access(on)   // C3198  
```