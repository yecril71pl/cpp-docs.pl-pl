---
title: "Kompilatora (poziom 3) ostrzeżenie C4635 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4635
dev_langs: C++
helpviewer_keywords: C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 00a831acaa172dfc24c4c39643b223ed6319a9e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4635"></a>Kompilator C4635 ostrzegawcze (poziom 3)
Docelowy komentarza dokumentu XML: nieprawidłowo sformułowany kod XML: Przyczyna  
  
 Kompilator znaleziono problem związany z tagów XML.  Rozwiąż problem i skompiluj ponownie  
  
 Poniższy przykład generuje C4635:  
  
```  
// C4635.cpp  
// compile with: /doc /clr /W3 /c  
/// <summary>     
/// The contents of the folder have changed.  
/// <summary/>   // C4635  
  
// try the following line instead  
// /// </summary>  
public ref class Test {};  
```  
  
 Należy zauważyć, że dane wyjściowe dla tego przykładu mówi: **tag końcowy "członek" nie pasuje do tagu początkowego "Podsumowanie".**  
  
 Problem z tym przykładzie jest tagu końcowego dla \<podsumowania > jest źle sformułowana, i kompilator nie rozpoznaje ją jako \<podsumowania > tagu końcowego.  \<Elementu członkowskiego > tag jest osadzony w pliku .xdc przez kompilator w każdej kompilacji/doc.  Tak, w tym miejscu problemu jest to, że tag końcowy \</member >, jest niezgodny z poprzednich tagiem początkowym przetwarzany przez kompilator (\<podsumowania >.