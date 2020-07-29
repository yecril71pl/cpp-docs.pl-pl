---
title: Ostrzeżenie kompilatora (poziom 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 1d3af2b5629906679db46f6f669084c11a41f7ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233252"
---
# <a name="compiler-warning-level-1-c4503"></a>Ostrzeżenie kompilatora (poziom 1) C4503

> "*Identyfikator*": przekroczono długość nazwy dekoracyjnej, nazwa została obcięta

## <a name="remarks"></a>Uwagi

To ostrzeżenie kompilatora jest przestarzałe i nie jest generowane w kompilatorach programu Visual Studio 2017 i nowszych.

Nazwa dekoracyjna była dłuższa niż limit kompilatora (4096) i została obcięta. Aby uniknąć tego ostrzeżenia i obcinania, zmniejsz liczbę argumentów lub długość nazw używanych identyfikatorów. Nazwy dekoracyjne, które są dłuższe niż limit kompilatora, mają zastosowanie skrótu i nie są niebezpieczne dla kolizji nazw.

W przypadku korzystania ze starszej wersji programu Visual Studio to ostrzeżenie można wydać, gdy kod zawiera szablony wyspecjalizowane dla szablonów. Na przykład mapa map (z biblioteki standardowej języka C++). W takiej sytuacji można sprawić, aby elementy typedef były typu (na **`struct`** przykład), który zawiera mapę.

Można jednak zrezygnować z restrukturyzacji kodu.  Istnieje możliwość wysłania aplikacji generującej C4503, ale jeśli zostaną wyświetlone błędy czasu łącza w obciętym symbolu, może być trudniejsze do określenia typu symbolu w błędzie. Debugowanie może być również trudniejsze; Debuger może mieć trudne mapowanie nazwy symbolu na nazwę typu. Poprawność programu jest jednak niezależna od skróconej nazwy.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4503 w kompilatorach przed Visual Studio 2017:

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

Ten przykład pokazuje jeden ze sposobów, aby ponownie napisać kod w celu rozwiązania C4503:

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
