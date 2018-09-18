---
title: Kompilator ostrzeżenie (poziom 3) C4635 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7651012d4c48d420734a9c6ec2ff051718f82007
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038116"
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