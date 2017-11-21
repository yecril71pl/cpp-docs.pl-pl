---
title: "C2002 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2002
dev_langs: C++
helpviewer_keywords: C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8f6fc5983a462850581f69ca32dd7c305f9e847
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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