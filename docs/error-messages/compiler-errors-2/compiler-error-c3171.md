---
title: C3171 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ee6ee02511242e2af87024c741a3c97f3f3724d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257054"
---
# <a name="compiler-error-c3171"></a>C3171 błąd kompilatora
"module": nie można określić innych atrybutów modułu w projekcie  
  
 [Moduł](../../windows/module-cpp.md) znaleziono atrybuty z innym parametrem list w dwóch plików w kompilacji. Tylko jeden unikatowy `module` atrybut może być określona dla kompilacji.  
  
 Identyczne `module` atrybuty można określić więcej niż jednego pliku kodu źródłowego.  
  
 Na przykład jeśli następujące `module` znaleziono atrybuty:  
  
```  
// C3171.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];  
int main() {}  
```  
  
 a następnie  
  
```  
// C3171b.cpp  
// compile with: C3171.cpp  
// C3171 expected  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];  
```  
  
 Kompilator może wygenerować C3171 (Uwaga: wartości różnych wersji).