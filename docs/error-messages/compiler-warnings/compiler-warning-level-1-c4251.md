---
title: Kompilator ostrzeżenie (poziom 1) C4251 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad47d769dbfd09cc741be18598355dc34486bd54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045695"
---
# <a name="compiler-warning-level-1-c4251"></a>Kompilator ostrzeżenie (poziom 1) C4251

'Identyfikator': klasa "type" musi mieć interfejsu biblioteki dll, który ma być używany przez klientów klasy 'type2'

Aby ograniczyć możliwość uszkodzenia danych, podczas eksportowania do klasy za pomocą [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), upewnij się, że:

- Wszystkie dane statyczne, jest dostęp za pośrednictwem funkcji, które są eksportowane z biblioteki DLL.

- Nie śródwierszowych metody klasy można modyfikować danych statycznych.

- Żadne śródwierszowych metody klasy użyć funkcji CRT lub inne funkcje biblioteki dane statyczne (zobacz [potencjalne błędy przekazywania CRT obiektów w pliku DLL granicach](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) Aby uzyskać więcej informacji).

- Nie metody klasy (niezależnie od wartości inlining) można używać typów, których wystąpienia w pliku EXE i DLL mają różnice statyczne dane.

Można uniknąć, eksportowanie klas, definiując, które biblioteki DLL, która definiuje klasę z funkcjami wirtualnymi i funkcji, należy można wywołać w celu utworzenia wystąpienia i usuwania obiektów tego typu.  Następnie możesz po prostu wywołać funkcje wirtualne w typie.

Aby uzyskać więcej informacji na temat eksportowania szablonów, zobacz [ http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).

C4251 można zignorować, jeśli są pochodząca z typu w standardowej bibliotece języka C++, kompilacja wersji debugowania (**/mtd**) i których dotyczy _Container_base komunikat o błędzie kompilatora.

```
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```