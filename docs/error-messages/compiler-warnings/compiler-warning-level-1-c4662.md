---
title: Ostrzeżenie kompilatora (poziom 1) C4662
ms.date: 11/04/2016
f1_keywords:
- C4662
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
ms.openlocfilehash: ff8a2f73523802a7c62e999be00c77400fbc0f23
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051430"
---
# <a name="compiler-warning-level-1-c4662"></a>Ostrzeżenie kompilatora (poziom 1) C4662

jawne utworzenie wystąpienia; Klasa szablonu "Identifier1" nie ma definicji, z której można specjalizacji "identifier2"

Określona Klasa szablonu została zadeklarowana, ale nie została zdefiniowana.

## <a name="example"></a>Przykład

```cpp
// C4662.cpp
// compile with: /W1 /LD
template<class T, int i> class MyClass; // no definition
template MyClass< int, 1>;              // C4662
```