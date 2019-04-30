---
title: Kompilator ostrzeżenie (poziom 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: e9fcb4356d993d86b622fd49c4a75d587554f7c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388608"
---
# <a name="compiler-warning-level-1-c4055"></a>Kompilator ostrzeżenie (poziom 1) C4055

> "*konwersji*": ze wskaźnika danych "*type1*"do wskaźnika funkcji"*type2*"

## <a name="remarks"></a>Uwagi

**Przestarzałe:** To ostrzeżenie nie jest generowany w programie Visual Studio 2017 i nowsze wersje.

Wskaźnik danych jest (prawdopodobnie nieprawidłowo) rzutowany na wskaźnik funkcji. To jest ostrzeżenia poziomu 1, w obszarze/za włączonego ostrzeżenia poziomu 4 pod /Ze.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4055:

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

Pod /Ze to jest ostrzeżenie poziom 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
