---
title: Kompilator ostrzeżenie (poziom 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 6e0e80d465d77bd4fe99fbcaa98e289b8a4c8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349688"
---
# <a name="compiler-warning-level-2-c4275"></a>Kompilator ostrzeżenie (poziom 2) C4275

> inne niż - klasy interfejsu biblioteki DLL*class_1*"używany jako podstawowa dla klasy interfejsu biblioteki DLL"*class_2*"

Wyeksportowanej klasy pochodzi z klasy, która nie została wyeksportowana.

Aby ograniczyć możliwość uszkodzenia danych, podczas eksportowania do klasy za pomocą [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), upewnij się, że:

- Wszystkie dane statyczne odbywa się za pośrednictwem funkcji, które są eksportowane z biblioteki DLL.

- Nie śródwierszowych metody klasy można modyfikować danych statycznych.

- Żadne śródwierszowych metody klasy, użyj funkcji CRT lub inne jego funkcje biblioteki, które używają danych statycznych.

- Brak funkcji śródwierszowych klasy, użyj funkcji CRT lub inne funkcje biblioteki gdzie uzyskujesz dostęp do danych statycznych.

- Nie metody klasy (niezależnie od wartości inlining) można używać typów, których wystąpienia w pliku EXE i DLL mają różnice statyczne dane.

Można uniknąć, eksportowanie klas, definiując, które biblioteki DLL, która definiuje klasę z funkcjami wirtualnymi i funkcji, należy można wywołać w celu utworzenia wystąpienia i usuwania obiektów tego typu.  Następnie możesz po prostu wywołać funkcje wirtualne w typie.

C4275 można zignorować w programie Visual C++, jeśli są pochodząca z typu w standardowej bibliotece języka C++, kompilacja wersji debugowania (**/mtd**) i gdzie komunikat o błędzie kompilatora odnosi się do `_Container_base`.

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```