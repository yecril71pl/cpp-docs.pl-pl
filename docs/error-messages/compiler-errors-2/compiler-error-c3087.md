---
title: C3087 błąd kompilatora
ms.date: 11/04/2016
f1_keywords:
- C3087
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
ms.openlocfilehash: 43044e0708ce9c30099c7d25935a8ff9605f45ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243261"
---
# <a name="compiler-error-c3087"></a>C3087 błąd kompilatora

"named_argument": wywołanie "attribute" już inicjuje tą składową

Argument nazwany została określona w tym samym bloku atrybutu jako argument bez nazwy dla tej samej wartości. Należy określić tylko argument nazwany lub bez nazwy.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3087.

```
// C3087.cpp
// compile with: /c
[idl_quote("quote1", text="quote2")];   // C3087
[idl_quote(text="quote3")];   // OK
[idl_quote("quote4")];   // OK
```