---
title: Kompilator ostrzeżenie (poziom 1) C4076 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 928b0a78c09773e334c1a291877b74304dab66ec
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198481"
---
# <a name="compiler-warning-level-1-c4076"></a>Kompilator ostrzeżenie (poziom 1) C4076

> "*modyfikatora typu*": nie można używać z typem "*typename*"

## <a name="remarks"></a>Uwagi

Modyfikator typu, czy jest to **podpisany** lub **niepodpisane**, nie można używać z typem danych nie jest liczbą całkowitą. *Modyfikator typu* jest ignorowana.
  
## <a name="example"></a>Przykład  

Poniższy przykład spowoduje wygenerowanie C4076; Aby rozwiązać ten problem, Usuń **niepodpisane** modyfikatora typu:

```cpp
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```