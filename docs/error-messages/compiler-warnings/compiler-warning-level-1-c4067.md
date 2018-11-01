---
title: Kompilator ostrzeżenie (poziom 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 012866e328433ec9511782c26a39265481ff4940
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541193"
---
# <a name="compiler-warning-level-1-c4067"></a>Kompilator ostrzeżenie (poziom 1) C4067

> nieoczekiwane tokeny po dyrektywie preprocesora - oczekiwano nowego wiersza

## <a name="remarks"></a>Uwagi

Kompilator znalezione i zignorowane dodatkowe znaki następujące dyrektywy preprocesora. Może to być spowodowane przez wszelkie nieoczekiwane znaki, że typową przyczyną jest zabłąkany średnik, po zakończeniu dyrektywy. Komentarze nie powoduje to ostrzeżenie. **/Za** — opcja kompilatora umożliwia to ostrzeżenie, aby uzyskać więcej dyrektywy preprocesora niż domyślne ustawienie.

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

Aby rozwiązać to ostrzeżenie, usuń znaki zabłąkany lub przenieść je do blok komentarza. Niektórych ostrzeżeń C4067 mogą być wyłączone przez usunięcie **/Za** — opcja kompilatora.

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