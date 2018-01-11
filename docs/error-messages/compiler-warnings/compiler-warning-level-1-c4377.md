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
ms.workload: cplusplus
ms.openlocfilehash: b2cf61aa35bcfc40a40febb9e066caba6decd682
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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