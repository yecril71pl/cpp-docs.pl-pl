---
title: Błąd kompilatora C2813
ms.date: 11/04/2016
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
ms.openlocfilehash: b36e966d897b1a3f9a4f601ef281091160da34c3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750939"
---
# <a name="compiler-error-c2813"></a>Błąd kompilatora C2813

\#import nie jest obsługiwany z/MP

C2813 jest emitowany, jeśli w poleceniu kompilatora określono opcję kompilatora **/MP** i dwa lub więcej plików do skompilowania, a co najmniej jeden plik zawiera dyrektywę preprocesora[#import](../../preprocessor/hash-import-directive-cpp.md) . Dyrektywa [#import](../../preprocessor/hash-import-directive-cpp.md) generuje C++ klasy z typów w określonej bibliotece typów, a następnie zapisuje te klasy do dwóch plików nagłówkowych. Dyrektywa [#import](../../preprocessor/hash-import-directive-cpp.md) nie jest obsługiwana, ponieważ jeśli wiele jednostek kompilacji zaimportuje tę samą bibliotekę typów, te jednostki powodują konflikt w przypadku próby zapisu tych samych plików nagłówkowych w tym samym czasie.

Ten błąd kompilatora i opcja kompilatora **/MP** są nowe w programie Visual Studio 2008.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2813. Wiersz polecenia w komentarzu "Kompiluj z:" wskazuje kompilatorowi, aby użyć opcji kompilatora **/MP** i **/c** do kompilowania kilku plików. Co najmniej jeden z plików zawiera dyrektywę [#import](../../preprocessor/hash-import-directive-cpp.md) . Ten sam plik jest używany dwa razy do testowania tego przykładu.

```cpp
// C2813.cpp
// compile with: /MP /c C2813.cpp C2813.cpp
#import "C:\windows\system32\stdole2.tlb"   // C2813
int main()
{
}
```
