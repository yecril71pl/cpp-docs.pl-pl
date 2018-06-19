---
title: C2567 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2567
dev_langs:
- C++
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05f89362f36a6ba576e9829153f0d8931c4975c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229692"
---
# <a name="compiler-error-c2567"></a>C2567 błąd kompilatora
Nie można otworzyć metadanych w "file", plik może mieć został usunięty lub przeniesiony  
  
 Plik metadanych, który został przywołany w źródłowym (z `#using`) nie został odnaleziony w tym samym katalogu przez proces zapleczu kompilatora jak przez proces frontonu kompilatora. Zobacz [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md) Aby uzyskać więcej informacji.  
  
 C2567 możliwe przyczyny kompilacji z **/c** na jednym komputerze, a następnie spróbuj Generowanie łączonych kodów czasowych na innym komputerze. Aby uzyskać więcej informacji, zobacz [opcję/LTCG (Generowanie kodu w czasie Link)](../../build/reference/ltcg-link-time-code-generation.md)).  
  
 Może też wskazywać, że komputer ma nie więcej pamięci.  
  
 Aby rozwiązać ten problem, upewnij się, jego pliku metadanych jest na wszystkich etapach procesu kompilacji w tej samej lokalizacji katalogu.