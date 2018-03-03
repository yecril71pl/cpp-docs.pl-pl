---
title: "C2002 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a2cbd21c27cff3effad69b19f42eeaecacf20d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2002"></a>C2002 błąd kompilatora
Nieprawidłowa stała znaków dwubajtowych  
  
 Stała znaków wielobajtowych jest nieprawidłowa.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Szerokich znaków stała zawiera więcej bajtów niż oczekiwano.  
  
2.  Standardowy nagłówek STDDEF.h nie jest włączony.  
  
3.  Znaki dwubajtowe nie może zostać połączony z zwykłej literały.  
  
4.  Szerokich znaków stała musi być poprzedzona znakiem "L":  
  
    ```  
    L'mbconst'  
    ```  
  
5.  Dla Microsoft C++ argumenty tekst dyrektywy preprocesora muszą być ASCII. Na przykład dyrektywy `#pragma message(L"string")`, jest nieprawidłowy.