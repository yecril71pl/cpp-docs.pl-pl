---
title: Ostrzeżenie kompilatora (poziom 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 9f261d3deb7f1cac8cd5c60b920e0be49bc8b7a6
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032333"
---
# <a name="compiler-warning-level-1-c4251"></a>Ostrzeżenie kompilatora (poziom 1) C4251

> '*type*' : class '*type1*' musi mieć interfejs DLL do użycia przez klientów klasy '*type2*'

## <a name="remarks"></a>Uwagi

Aby zminimalizować możliwość uszkodzenia danych podczas eksportowania klasy zadeklarowanej jako [__declspec(dllexport),](../../cpp/dllexport-dllimport.md)należy zapewnić, że:

- Wszystkie dane statyczne są dostępne za pośrednictwem funkcji, które są eksportowane z biblioteki DLL.

- Żadne wbudowane metody klasy można modyfikować dane statyczne.

- Żadne wbudowane metody klasy nie używają funkcji CRT lub innych funkcji biblioteki, które używają danych statycznych. Aby uzyskać więcej informacji, zobacz [Potencjalne błędy przekazywania obiektów CRT przez granice biblioteki DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

- Żadne metody klasy (czy inlined lub nie) można użyć typów, w których wystąpienia w EXE i DLL mają różnice danych statycznych.

Można uniknąć problemów podczas eksportowania klasy z biblioteki DLL: Zdefiniuj klasę, aby mieć funkcje wirtualne i funkcje do tworzenia wystąpienia i usuwania obiektów typu. Następnie można po prostu wywołać funkcje wirtualne na typ.

C4251 można zignorować, jeśli klasa pochodzi od typu w bibliotece standardowej C++, kompilujesz zwolnienie debugowania (**/MTd**) i gdzie odnosi się komunikat o błędzie kompilatora `_Container_base`.

## <a name="example"></a>Przykład

Ten przykład eksportuje `VecWrapper` wyspecjalizowaną `std::vector`klasę pochodzącą z .

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
