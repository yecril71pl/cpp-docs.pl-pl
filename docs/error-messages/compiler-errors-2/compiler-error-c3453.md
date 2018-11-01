---
title: Błąd kompilatora C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 2b3288d02c611bf6785ca1ea7757e2283d889050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472725"
---
# <a name="compiler-error-c3453"></a>Błąd kompilatora C3453

"attribute": atrybut nie zastosowany, ponieważ kwalifikator "assembly" nie pasują.

Zestaw lub moduł atrybuty na poziomie można określić tylko jako autonomiczny instrukcje.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3453.

```
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```