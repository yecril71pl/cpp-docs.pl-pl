---
title: C2002 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01124fc839d6e788ff2dccae325f01f7d4337f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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