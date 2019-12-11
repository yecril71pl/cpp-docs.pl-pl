---
title: Ostrzeżenie kompilatora (poziom 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: fd3bf6c1b14c6dae8e2fa95a54e2d4fbc4f295c5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991852"
---
# <a name="compiler-warning-level-3-c4635"></a>Ostrzeżenie kompilatora (poziom 3) C4635

Obiekt docelowy komentarza dokumentu XML: nieprawidłowo sformułowany kod XML: Przyczyna

Kompilator wykrył jakiś problem z tagami XML.  Usuń problem i ponownie skompiluj

Poniższy przykład generuje C4635:

```cpp
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

Zwróć uwagę, że dane wyjściowe dla tego przykładu brzmią: **tag końcowy "member" jest niezgodny z tagiem początkowym "Summary".**

Problem z tym przykładem polega na tym, że tag końcowy > podsumowania \<jest źle sformułowany, a kompilator nie rozpoznaje go jako \<podsumowania > końcowego.  Tag > składowej \<jest osadzony w pliku XDC przez kompilator w każdej kompilacji/doc.  Dlatego problem polega na tym, że tag końcowy \</member >, nie pasuje do poprzedniego tagu początkowego, który został przetworzony przez kompilator (\<> podsumowania.
