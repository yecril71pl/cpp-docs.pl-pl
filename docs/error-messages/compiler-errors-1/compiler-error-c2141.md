---
title: Błąd kompilatora C2141
ms.date: 11/04/2016
f1_keywords:
- C2141
helpviewer_keywords:
- C2141
ms.assetid: 10cf770f-0500-4220-ac90-a863b7ea5fe6
ms.openlocfilehash: 89395fa3419d79fa4dec3fecf9acfc681590d825
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353569"
---
# <a name="compiler-error-c2141"></a>Błąd kompilatora C2141

Przekroczono rozmiar tablicy

Tablica przekracza limit 2GB. Zmniejsz rozmiar tablicy.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2141.

```
// C2141.cpp
// processor: IPF
class A {
   short m_n;
};

int main()
{
   A* pA = (A*)(-1);
   pA = new A[0x8000000000000001];   // C2141

   A* pA2 = (A*)(-1);
   pA2 = new A[0x80000000000000F];   // OK
}
```