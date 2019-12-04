---
title: Błąd kompilatora C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: 37129c198096be91a8104aedcb508732d79e3630
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738313"
---
# <a name="compiler-error-c3492"></a>Błąd kompilatora C3492

"var": nie można przechwycić elementu członkowskiego Unii anonimowej

Nie można przechwycić elementu członkowskiego nienazwanej Unii.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nadaj Unii nazwę i przekaż kompletną strukturę Union do listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3492, ponieważ przechwytuje element członkowski anonimowej Unii:

```cpp
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

Poniższy przykład rozwiązuje C3492 przez nadanie nazwy Unii i przekazanie kompletnej struktury Union do listy przechwytywania wyrażenia lambda:

```cpp
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

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
