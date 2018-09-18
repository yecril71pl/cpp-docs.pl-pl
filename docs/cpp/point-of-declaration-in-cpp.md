---
title: Punkt deklaracji w języku C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68ac24fcfe35701dd75d74800661aa5e41c005f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072071"
---
# <a name="point-of-declaration-in-c"></a>Punkt deklaracji w kodzie C++

Nazwa jest uważany za zgłaszane natychmiast po jego deklaratora, ale przed jego Inicjator (opcjonalnie). (Aby uzyskać więcej informacji dotyczących deklaratorów, zobacz [deklaracje i definicje](declarations-and-definitions-cpp.md).)

Rozważmy następujący przykład:

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

Punkt deklaracji były *po* inicjowania, a następnie lokalnej `dVar` będzie można zainicjować 7.0, wartość zmiennej globalnej `dVar`. Jednakże, ponieważ nie jest tak, `dVar` jest ustawiana na wartość niezdefiniowana.

## <a name="see-also"></a>Zobacz także

[Zakres](../cpp/scope-visual-cpp.md)