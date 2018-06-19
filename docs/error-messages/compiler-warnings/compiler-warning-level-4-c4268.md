---
title: Kompilatora (poziom 4) ostrzeżenie C4268 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef62649af39df950c3966ef93dddb6c71ec2fd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293374"
---
# <a name="compiler-warning-level-4-c4268"></a>Kompilator C4268 ostrzegawcze (poziom 4)
"identyfikator": "const" statyczne/globalne dane zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora, który wypełnił obiekt zerami  
  
 A **const** globalnych lub statycznych wystąpienia klasy nieuproszczony została zainicjowana przy użyciu generowane przez kompilator domyślnego konstruktora.  
  
## <a name="example"></a>Przykład  
  
```  
// C4268.cpp  
// compile with: /c /LD /W4  
class X {  
public:  
   int m_data;  
};  
  
const X x1;   // C4268  
```  
  
 Ponieważ jest to wystąpienie klasy **const**, wartość `m_data` nie można zmienić.