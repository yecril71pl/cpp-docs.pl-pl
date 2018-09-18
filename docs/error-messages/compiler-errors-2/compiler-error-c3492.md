---
title: Błąd kompilatora C3492 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3492
dev_langs:
- C++
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54b3689a6ee565788e2a469a8321727a9fdd822f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089219"
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