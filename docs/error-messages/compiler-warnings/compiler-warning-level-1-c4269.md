---
title: Kompilatora (poziom 1) ostrzeżenie C4269 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e393c657e12f84d3cadfacd469e35e3472a39d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281794"
---
# <a name="compiler-warning-level-1-c4269"></a>Kompilator C4269 ostrzegawcze (poziom 1)
"identyfikator": "const" zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora danych zwrócił niepewne wyniki  
  
 A **const** automatyczne wystąpienia klasy nieuproszczony została zainicjowana przy użyciu generowane przez kompilator domyślnego konstruktora.  
  
## <a name="example"></a>Przykład  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 Ponieważ to wystąpienie klasy jest generowany na stosie początkowej wartości `m_data` może być dowolna. Ponieważ jest także **const** wystąpienie wartość `m_data` nigdy nie można zmienić.