---
title: Błąd kompilatora C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: 468fc5e8cb6b3a76880f12fe0aab14810f458a90
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741355"
---
# <a name="compiler-error-c3838"></a>Błąd kompilatora C3838

nie można jawnie dziedziczyć po elemencie "Type"

Określony `type` nie może działać jako klasa bazowa w żadnej klasie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3838:

```cpp
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
