---
title: Kompilatora (poziom 1) ostrzeżenie C4377 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef049f85cd17bfeaba243b84da9fca93ae4036b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274784"
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