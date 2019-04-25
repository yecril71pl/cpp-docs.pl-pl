---
title: Kompilator ostrzeżenie (poziom 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 94c88511d87c3adf3cf5687a94948c83ebc5b3d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160981"
---
# <a name="compiler-warning-level-1-c4503"></a>Kompilator ostrzeżenie (poziom 1) C4503

> "*identyfikator*": przekroczona długość nazwy, dekorowanej nazwa została obcięta

## <a name="remarks"></a>Uwagi

Ostrzeżenie kompilatora jest przestarzała i nie są generowane w Visual Studio 2017 i nowszym kompilatory.

Również nazwę uzupełnioną trwało dłużej niż limit kompilatora (4096) i zostały obcięte. Aby uniknąć tego ostrzeżenia i obcinania, Zmniejsz liczbę argumentów lub długości nazwy identyfikatory używane. Nazw, które są dłuższy niż limit kompilatora skrót zastosowane i nie są zagrożone kolizji nazw ozdobionych.

Przy użyciu starszej wersji programu Visual Studio, mogą być wystawiane to ostrzeżenie, jeśli kod zawiera szablony przeznaczone na szablonach wielokrotnie. Na przykład mapa map (ze standardowej biblioteki C++). W takiej sytuacji można zmienić swoje definicje typów typu ( **struktury**, na przykład) który zawiera mapę.

Może jednak zadecydować, nie restrukturyzacji swój kod.  Istnieje możliwość dostarczania aplikacji, która generuje C4503, ale jeśli na obcięte symbolu występują błędy czasu łącze, może być trudniejsze można ustalić typu symbolu w błędzie. Debugowanie może również być trudniejsze; debuger może mieć problemy mapowania nazwy symbolu do nazwy typu. Jednak poprawność programu, jest niezależny od skróconą nazwę.

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

W tym przykładzie przedstawiono jeden ze sposobów do przepisania kodu można rozpoznać C4503:

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