---
title: "Kompilatora (poziom 1) ostrzeżenie C4228 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4228
dev_langs: C++
helpviewer_keywords: C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ac01b49a45a64d1a4e1480a64410726c61975c51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4228"></a>Kompilator C4228 ostrzegawcze (poziom 1)
użyto niestandardowego rozszerzenia: kwalifikatory po przecinku na liście deklaratorów są ignorowane.  
  
 Użyj kwalifikatorów, takich jak **const** lub `volatile` po przecinek podczas deklarowania zmiennych rozszerzenia Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
## <a name="example"></a>Przykład  
  
```  
// C4228.cpp  
// compile with: /W1  
int j, const i = 0;  // C4228  
int k;  
int const m = 0;  // ok  
int main()  
{  
}  
```