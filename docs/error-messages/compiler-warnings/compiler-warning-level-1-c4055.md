---
title: Kompilatora (poziom 1) ostrzeżenie C4052 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4055
dev_langs:
- C++
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47d7d8891b589dc8205b0d799f88466c1e7d8a59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278983"
---
# <a name="compiler-warning-level-1-c4055"></a>Kompilator C4055 ostrzegawcze (poziom 1)

> "*konwersji*": ze wskaźnika danych "*type1*"do wskaźnika funkcji"*type2*"

## <a name="remarks"></a>Uwagi

**Wygasłe:** to ostrzeżenie nie jest generowany przez Visual Studio 2017 i nowszych wersjach.

Wskaźnik danych jest rzutowane (prawdopodobnie nieprawidłowo) na wskaźnik funkcji. Jest to ostrzeżenia poziomu 1, w obszarze /Za i ostrzeżenie poziom 4 w obszarze /Ze.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4055:

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

W obszarze /Ze to ostrzeżenie poziom 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
