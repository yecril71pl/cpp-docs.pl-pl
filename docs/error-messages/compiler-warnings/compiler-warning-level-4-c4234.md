---
title: "Kompilatora (poziom 4) ostrzeżenie C4234 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4234
dev_langs: C++
helpviewer_keywords: C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86a44dfc09e3b0bcb0744115ce4ddfaf8d96f258
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4234"></a>Kompilator C4234 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: słowo kluczowe "— słowo kluczowe" zarezerwowane do użytku w przyszłości  
  
 Kompilator nie implementuje jeszcze słowo kluczowe, które są używane.  
  
 To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład, aby przekształcić C4234 ostrzeżenie poziom 4 problem  
  
```  
#pragma warning(2:4234)  
```  
  
 w pliku kodu źródłowego.