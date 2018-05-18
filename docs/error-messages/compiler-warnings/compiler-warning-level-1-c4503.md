---
title: Kompilatora (poziom 1) ostrzeżeń C4503 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f60fdb44c5368ccc5c5f089002614332d95a63fe
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="compiler-warning-level-1-c4503"></a>Kompilatora (poziom 1) ostrzeżeń C4503

> "*identyfikator*": przekroczona długość nazwy, dekorowanej nazwa została obcięta

## <a name="remarks"></a>Uwagi

To ostrzeżenie kompilatora jest przestarzały i nie jest generowany w Visual Studio 2017 i nowszym kompilatory.

Nazwa był dłuższy niż limit kompilatora (4096) i została obcięta. Aby uniknąć tego ostrzeżenia i obcinania, Zmniejsz liczbę argumentów lub długość nazwy identyfikatory używane. Dekorowane nazwy, które są dłużej niż limit kompilatora skrót zastosowane i nie są zagrożone kolizję nazw.

Przy użyciu starszej wersji programu Visual Studio, mogą być wystawiane to ostrzeżenie, jeśli kod zawiera szablony przeznaczone na szablonach wielokrotnie. Na przykład mapa mapy (z standardowa biblioteka C++). W takiej sytuacji można wprowadzić Twoje definicje typów typu ( **struktury**, na przykład) zawierający mapy.

Jednak możesz nie restrukturyzacji kodu.  Można wydać aplikację, która generuje C4503, ale jeśli występują błędy czasu łącza na symbol obcięty, może być trudno jest określić typ symbolu w dzienniku błędów. Debugowanie może również być trudniejsze; debuger może być difficultly mapowania nazwy symbolu nazwy typu. Poprawność programu, jednak nie mają wpływu skróconą nazwę.

## <a name="example"></a>Przykład

Poniższy przykład powoduje wygenerowanie C4503 w kompilatory przed Visual Studio 2017:

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

Ten przykład przedstawia sposób ponownego zapisywania swój kod, aby rozwiązać C4503:

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```