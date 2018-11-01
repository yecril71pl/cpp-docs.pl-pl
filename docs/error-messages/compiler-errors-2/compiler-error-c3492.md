---
title: Błąd kompilatora C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: 53dd22368aee5e0de9eca1349eb4d7dd3ed1c570
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485010"
---
# <a name="compiler-error-c3492"></a>Błąd kompilatora C3492

"var": nie można dokonać przechwytu składowej z anonimowej Unii

Nie można dokonać przechwytu składowej Unii, bez nazwy.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nazwij Unii i przekazać pełną strukturę złożenia do listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3492, ponieważ to przechwycenie składowej z anonimowej Unii:

```
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

## <a name="example"></a>Przykład

Poniższy przykład usuwa C3492, nadając nazwę Unii i przekazując pełną strukturę złożenia do listy przechwytywania wyrażenia lambda:

```
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)