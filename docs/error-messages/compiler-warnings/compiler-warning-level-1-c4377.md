---
title: "Kompilatora (poziom 1) ostrzeżenie C4377 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4377
dev_langs: C++
helpviewer_keywords: C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e52479aac07cdb31f62b20cb6c865b48b270c2bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4377"></a>Kompilator C4377 ostrzegawcze (poziom 1)
typy natywne są domyślnie; prywatne -d1PrivateNativeTypes jest przestarzały  
  
 W poprzednich wersjach, zostały domyślnie i — opcja kompilatora wewnętrzne, nieudokumentowanej publicznego natywnych typów w zestawach (**/d1PrivateNativeTypes**) został użyty do je skonfigurować.  
  
 Wszystkie typy natywnego i CLR, teraz są domyślnie w zestawie, prywatne, **/d1PrivateNativeTypes** nie jest już potrzebne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4377.  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```