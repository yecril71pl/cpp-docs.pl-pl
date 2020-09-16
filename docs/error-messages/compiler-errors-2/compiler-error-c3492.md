---
title: Błąd kompilatora C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: bdaeb8797eb71b205f737d08e74430f161cb8caa
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686551"
---
# <a name="compiler-error-c3492"></a>Błąd kompilatora C3492

"var": nie można przechwycić elementu członkowskiego Unii anonimowej

Nie można przechwycić elementu członkowskiego nienazwanej Unii.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nadaj Unii nazwę i przekaż kompletną strukturę Union do listy przechwytywania wyrażenia lambda.

## <a name="examples"></a>Przykłady

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
