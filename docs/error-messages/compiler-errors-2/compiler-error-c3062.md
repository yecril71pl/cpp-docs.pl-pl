---
title: C3062 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da507511cb5f091d5d9432bbfeb36951e3f43c6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250569"
---
# <a name="compiler-error-c3062"></a>C3062 błąd kompilatora
Instrukcja "enum": moduł wyliczający wymaga wartości, ponieważ podstawowy typ to 'type'  
  
 Można określić typu podstawowego dla wyliczenia. Jednak niektóre typy wymagają można przypisać wartości do każdego modułu wyliczającego.  
  
 Aby uzyskać więcej informacji na wyliczenia, zobacz [Wylicz klasy](../../windows/enum-class-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C3062:  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```