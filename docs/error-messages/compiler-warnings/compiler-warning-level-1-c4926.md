---
title: Kompilatora (poziom 1) ostrzeżenie C4926 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4926
dev_langs:
- C++
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527c03d4f71048064c2120f7cfa9730de198fd46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290858"
---
# <a name="compiler-warning-level-1-c4926"></a>Kompilator C4926 ostrzegawcze (poziom 1)
'Identyfikator': symbol jest już zdefiniowany: atrybuty zostały zignorowane  
  
 Deklaracja przekazująca dalej został znaleziony, ale oparte na atrybutach konstrukcję o tej samej nazwie już istnieje. Deklaracja przekazująca dalej atrybuty są ignorowane.  
  
 Poniższy przykład generuje C4926:  
  
```  
// C4926.cpp  
// compile with: /W1  
[module(name="MyLib")];  
  
[coclass]  
struct a {  
};  
  
[coclass]  
struct a;   // C4926  
  
int main() {  
}  
```