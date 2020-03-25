---
title: Ostrzeżenie kompilatora (poziom 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 8a723b7ce7fc79fb6be9c9dd2b500631098622b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163222"
---
# <a name="compiler-warning-level-1-c4251"></a>Ostrzeżenie kompilatora (poziom 1) C4251

"Identyfikator": Klasa "Type" musi mieć interfejs dll, który ma być używany przez klientów klasy "type2"

Aby zminimalizować prawdopodobieństwo uszkodzenia danych podczas eksportowania klasy z [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), upewnij się, że:

- Wszystkie dane statyczne są dostępne za pośrednictwem funkcji wyeksportowanych z biblioteki DLL.

- Żadna z nieliniowych metod klasy nie może modyfikować danych statycznych.

- Żadna z nieliniowych metod klasy nie korzysta z funkcji CRT lub innych funkcji biblioteki, użyj danych statycznych (zobacz [potencjalne błędy przekazywania obiektów CRT między granicami bibliotek DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) , aby uzyskać więcej informacji).

- Żadna metoda klasy (bez względu na dekreślenie) może używać typów, w których wystąpienie w EXE i DLL ma różnice danych statycznych.

Można uniknąć eksportowania klas przez zdefiniowanie biblioteki DLL, która definiuje klasę z funkcjami wirtualnymi, oraz funkcje, które można wywołać w celu utworzenia wystąpienia i usunięcia obiektów typu.  Następnie można wywołać funkcje wirtualne w typie.

C4251 można zignorować, jeśli pochodzą z typu w bibliotece C++ standardowej, kompilując wydanie debugowania ( **/MTD**) i miejsce, w którym komunikat o błędzie kompilatora odnosi się do _Container_base.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```
