---
title: Kompilator ostrzeżenie (poziom 4) C4263 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4263
dev_langs:
- C++
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf93a010ac10b8b55bd22b9ab2db12d77a02c13a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079638"
---
# <a name="compiler-warning-level-4-c4263"></a>Kompilator ostrzeżenie (poziom 4) C4263

'Funkcja': funkcja składowa nie zastępuje żadnej funkcji składowej wirtualnej klasy bazowej

Definicja funkcji klasa ma taką samą nazwę jak funkcja wirtualna klasa bazowa, ale nie ten sam numer lub typ argumentów. Spowoduje to skutecznie ukrycie funkcji wirtualnej w klasie bazowej.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4263:

```
// C4263.cpp
// compile with: /W4
#pragma warning(default:4263)
#pragma warning(default:4264)
class B {
public:
   virtual void func();
};

class D : public B {
   void func(int);   // C4263
};

int main() {
}
```