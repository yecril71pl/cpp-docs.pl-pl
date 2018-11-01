---
title: Błąd kompilatora C3807
ms.date: 11/04/2016
f1_keywords:
- C3807
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
ms.openlocfilehash: b5599914666af95a29667acc1ad4ad35eef7608f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591129"
---
# <a name="compiler-error-c3807"></a>Błąd kompilatora C3807

"type": klasa z atrybutem ComImport nie może pochodzić od "type2", tylko implementacja interfejsu jest dozwolona

Typ, który pochodzi od <xref:System.Runtime.InteropServices.ComImportAttribute> można tylko zaimplementować interfejs.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3807.

```
// C3807.cpp
// compile with: /clr /c
ref struct S {};
interface struct I {};

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 : S {};   // C3807
ref struct S2 : I {};
```