---
title: Kompilator ostrzeżenie (poziom 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: 21873a883b19924ce3ef41511d65f8ae640875f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479238"
---
# <a name="compiler-warning-level-3-c4635"></a>Kompilator ostrzeżenie (poziom 3) C4635

Docelowy komentarza dokumentu XML: niewłaściwie sformułowany kod XML: Przyczyna

Kompilator znaleziono problem związany z tagów XML.  Rozwiąż problem i ponowna kompilacja

Poniższy przykład spowoduje wygenerowanie C4635:

```
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

Należy zauważyć, że dane wyjściowe, w tym przykładzie jest wyświetlany komunikat: **tag końcowy "członek" pasuje do tagu początkowego "Podsumowanie".**

Problem z tego przykładu jest tagu końcowego dla \<podsumowania > jest źle sformułowany i kompilator rozpoznaje je jako \<podsumowania > tagu końcowego.  \<Składowej > tag jest osadzony w pliku .xdc przez kompilator w każdej kompilacji/doc.  Dlatego problem polega na tym, tagu końcowego \</member >, pasuje do poprzedniego tagu początkowego, które kompilator przetwarzane (\<podsumowania >.