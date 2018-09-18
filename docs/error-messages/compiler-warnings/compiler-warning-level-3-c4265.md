---
title: Kompilator ostrzeżenie (poziom 3) C4265 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4265
dev_langs:
- C++
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0df54714038ab0fb6020e34aa35d677af5e899b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016133"
---
# <a name="compiler-warning-level-3-c4265"></a>Kompilator ostrzeżenie (poziom 3) C4265

"class": klasa ma funkcje wirtualne, ale destruktor nie jest wirtualny

Gdy klasa ma funkcje wirtualne, ale Niewirtualny destruktor, obiektów tego typu może nie zostać zniszczone prawidłowo kiedy niszczony jest klasy za pomocą wskaźnika klasy podstawowej.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4265:

```
// C4265.cpp
// compile with: /W3 /c
#pragma warning(default : 4265)
class B
{
public:
   virtual void vmf();

   ~B();
   // try the following line instead
   // virtual ~B();
};   // C4265

int main()
{
   B b;
}
```