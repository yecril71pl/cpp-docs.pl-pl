---
title: Kompilator ostrzeżenie (poziom 2) C4275 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cb8f397243bb6531f33ac5e444914cfa36e5fe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022639"
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

Aby uzyskać więcej informacji na temat eksportowania szablonów, zobacz [ http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).

C4275 można zignorować w programie Visual C++, jeśli są pochodząca z typu w standardowej bibliotece języka C++, kompilacja wersji debugowania (**/mtd**) i których dotyczy _Container_base komunikat o błędzie kompilatora.

```
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```