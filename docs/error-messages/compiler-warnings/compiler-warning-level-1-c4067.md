---
title: Kompilatora (poziom 1) ostrzeżenie C4067 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee6b48327e8754f9388e0df8f43009a5be70c97
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255456"
---
# <a name="compiler-warning-level-1-c4067"></a>Kompilator C4067 ostrzegawcze (poziom 1)

> nieoczekiwane tokeny dyrektywie preprocesora - oczekiwano nowego wiersza

## <a name="remarks"></a>Uwagi

Kompilator znalezione i zignorowane dodatkowe znaki po dyrektywie preprocesora. Może to być spowodowane znaków nieoczekiwany że typową przyczyną jest stray średnika po zakończeniu dyrektywy. Komentarze nie powoduje to ostrzeżenie. **/Za** — opcja kompilatora umożliwia to ostrzeżenie, aby uzyskać więcej dyrektywy preprocesora niż domyślne ustawienie.

## <a name="example"></a>Przykład

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

Aby usunąć to ostrzeżenie, usuń znaki stray, lub przenieś je do blok komentarza. Określone ostrzeżenia C4067 mogą być wyłączone przez usunięcie **/Za** — opcja kompilatora.

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```