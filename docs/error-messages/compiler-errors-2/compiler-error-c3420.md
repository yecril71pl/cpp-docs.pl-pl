---
title: Błąd kompilatora C3420 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3420
dev_langs:
- C++
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3997bc0744bf1e1db34fe7ce1de666ebd3e3b8cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078572"
---
# <a name="compiler-error-c3420"></a>Błąd kompilatora C3420

"finalizator": finalizator nie może być wirtualny

Finalizator może zostać wywołana tylko-niemal z jego typie otaczającym. Dlatego jest błędem jest deklaracja finalizatora wirtualnego.

Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory w instrukcje: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3420.

```
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```