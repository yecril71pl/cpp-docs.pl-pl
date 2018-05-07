---
title: C2834 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eb4fb992f9213c4a4b456f786fd8f81308cec12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2834"></a>C2834 błąd kompilatora
"operator operator" musi być globalnie kwalifikowany  
  
 `new` i `delete` operatory są powiązane z klasy, których są one przechowywane. Rozpoznawanie zakresów nie będzie można wybrać wersję `new` lub `delete` z innej klasy. Aby zaimplementować wiele form `new` lub `delete` operatora, utworzyć wersję operatora z bardzo formalnych parametrów.