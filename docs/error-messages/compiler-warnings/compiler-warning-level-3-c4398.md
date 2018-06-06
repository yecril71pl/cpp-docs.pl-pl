---
title: Kompilatora (poziom 3) ostrzeżenie C4398 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c38ade6b75242fdd5144481e3415e914cb6773c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704617"
---
# <a name="compiler-warning-level-3-c4398"></a>Kompilator C4398 ostrzegawcze (poziom 3)

> "*zmiennej*": globalny obiekt dla procesu może nie działać poprawnie z wieloma domenami aplikacji; należy wziąć pod uwagę użycie __declspec(appdomain)

## <a name="remarks"></a>Uwagi

Funkcję wirtualną z [__clrcall](../../cpp/clrcall.md) konwencji wywoływania w typie natywnym powoduje utworzenie na vtable domeny aplikacji. Przekazanie zmiennej nie może rozwiązać poprawnie, gdy jest używany w wielu domenach aplikacji.

To ostrzeżenie można rozwiązać przez oznaczenie jawnie zmiennej `__declspec(appdomain)`. W wersjach programu Visual Studio przed Visual Studio 2017 to ostrzeżenie można rozwiązać przez kompilowania przy użyciu **/CLR: pure**, co czyni domyślnie zmienne globalne dla domeny appdomain. **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Aby uzyskać więcej informacji, zobacz [elementu appdomain](../../cpp/appdomain.md) i [i domen aplikacji Visual C++](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4398.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```