---
title: Kompilatora (poziom 1) ostrzeżenie C4829 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4829
dev_langs:
- C++
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c27ca268a3c873474cd4ed79a2b843642087c34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286542"
---
# <a name="compiler-warning-level-1-c4829"></a>Kompilator C4829 ostrzegawcze (poziom 1)
Prawdopodobnie niepoprawne parametry funkcji main. Należy wziąć pod uwagę "intmain (Platform::Array\<Platform::String ^ > ^ ARGV —)"  
  
 Określone funkcje, takie jak main, nie może przyjąć odwołanie parametrów typu. Podczas kompilacji powiedzie się, prawdopodobnie nie uruchomi się obraz wynikowy.  
  
 Poniższy przykład generuje C4829:  
  
```  
// C4829.cpp  
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp  
int main(Platform::String ^ s) {}   // C4829  
  
```