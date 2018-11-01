---
title: Kompilator ostrzeżenie (poziom 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 4126a1267b41cdf9c0161c7e85a9057b2a301d77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578467"
---
# <a name="compiler-warning-level-3-c4398"></a>Kompilator ostrzeżenie (poziom 3) C4398

> "*zmiennej*": globalny obiekt dla poszczególnych procesu mogą nie działać poprawnie z wieloma domenami aplikacji; należy wziąć pod uwagę użycie __declspec(appdomain)

## <a name="remarks"></a>Uwagi

Funkcja wirtualna, za pomocą [__clrcall](../../cpp/clrcall.md) konwencji wywoływania w typie natywnym powoduje utworzenie na vtable domeny aplikacji. Takie zmiennej nie może rozwiązać poprawnie, gdy jest używana w wielu domenach aplikacji.

To ostrzeżenie można rozwiązać, oznaczając jawnie zmiennej `__declspec(appdomain)`. W wersjach programu Visual Studio przed Visual Studio 2017, można usunąć to ostrzeżenie, kompilowania za pomocą **/CLR: pure**, co sprawia, że zmienne globalne dla domeny appdomain domyślnie. **/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Aby uzyskać więcej informacji, zobacz [appdomain](../../cpp/appdomain.md) i [domeny aplikacji i programu Visual C++](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4398.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```