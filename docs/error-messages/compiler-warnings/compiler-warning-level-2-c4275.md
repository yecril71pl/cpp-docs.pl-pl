---
title: Kompilator ostrzeżenie (poziom 2) C4275
ms.date: 11/04/2016
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 985a622e2c89306c453ae6c860d21e6265d0fff1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594327"
---
# <a name="compiler-warning-level-2-c4275"></a>Kompilator ostrzeżenie (poziom 2) C4275

inne niż - classkey interfejsu biblioteki DLL 'Identyfikator' używany jako bazowy classkey interfejsu biblioteki DLL 'Identyfikator'

Wyeksportowanej klasy pochodzi od klasy, która nie została wyeksportowana.

Aby ograniczyć możliwość uszkodzenia danych, podczas eksportowania do klasy za pomocą [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), upewnij się, że:

- Wszystkie dane statyczne odbywa się za pośrednictwem funkcji, które są eksportowane z biblioteki DLL.

- Nie śródwierszowych metody klasy można modyfikować danych statycznych.

- Nie śródwierszowych metody, klasy za pomocą funkcji CRT lub inne funkcje biblioteki używają danych statycznych.

- Brak funkcji śródwierszowych klasy, użyj funkcji CRT lub inne funkcje biblioteki where, na przykład, uzyskujesz dostęp do statycznych danych.

- Nie metody klasy (niezależnie od wartości inlining) można używać typów, których wystąpienia w pliku EXE i DLL mają różnice statyczne dane.

Można uniknąć, eksportowanie klas, definiując, które biblioteki DLL, która definiuje klasę z funkcjami wirtualnymi i funkcji, należy można wywołać w celu utworzenia wystąpienia i usuwania obiektów tego typu.  Następnie możesz po prostu wywołać funkcje wirtualne w typie.

C4275 można zignorować w programie Visual C++, jeśli są pochodząca z typu w standardowej bibliotece języka C++, kompilacja wersji debugowania (**/mtd**) i których dotyczy _Container_base komunikat o błędzie kompilatora.

```
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```