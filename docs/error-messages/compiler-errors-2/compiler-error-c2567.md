---
title: "C2567 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2567
dev_langs: C++
helpviewer_keywords: C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28cd1dc74e15ae3cd63286fc6de9c3508bb1d279
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2567"></a>C2567 błąd kompilatora
Nie można otworzyć metadanych w "file", plik może mieć został usunięty lub przeniesiony  
  
 Plik metadanych, który został przywołany w źródłowym (z `#using`) nie został odnaleziony w tym samym katalogu przez proces zapleczu kompilatora jak przez proces frontonu kompilatora. Zobacz [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md) Aby uzyskać więcej informacji.  
  
 C2567 możliwe przyczyny kompilacji z **/c** na jednym komputerze, a następnie spróbuj Generowanie łączonych kodów czasowych na innym komputerze. Aby uzyskać więcej informacji, zobacz [opcję/LTCG (Generowanie kodu w czasie Link)](../../build/reference/ltcg-link-time-code-generation.md)).  
  
 Może też wskazywać, że komputer ma nie więcej pamięci.  
  
 Aby rozwiązać ten problem, upewnij się, jego pliku metadanych jest na wszystkich etapach procesu kompilacji w tej samej lokalizacji katalogu.