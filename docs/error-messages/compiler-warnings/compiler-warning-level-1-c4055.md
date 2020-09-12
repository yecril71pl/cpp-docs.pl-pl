---
title: Ostrzeżenie kompilatora (poziom 1) C4055
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: 47883f60c3205125a8ee88b804c1d622b3ba0b41
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041032"
---
# <a name="compiler-warning-level-1-c4055"></a>Ostrzeżenie kompilatora (poziom 1) C4055

> "*Konwersja*": ze wskaźnika danych "*Type1*" do wskaźnika funkcji "*Type2*"

## <a name="remarks"></a>Uwagi

**Przestarzałe:** To ostrzeżenie nie jest generowane przez program Visual Studio 2017 i jego nowsze wersje.

Wskaźnik danych jest rzutowany (prawdopodobnie nieprawidłowo) do wskaźnika funkcji. Jest to ostrzeżenie poziomu 1 w obszarze/za i ostrzeżenie poziomu 4 w obszarze/ze.

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

W obszarze/ze jest to ostrzeżenie poziomu 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
