---
title: Ostrzeżenie kompilatora (poziom 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: ad12c1c27006a57c8339e9dad82e4d8e1a239a6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162000"
---
# <a name="compiler-warning-level-2-c4275"></a>Ostrzeżenie kompilatora (poziom 2) C4275

> Klasa "*class_1*" klasy innej niż dll została użyta jako podstawowa dla klasy interfejsu DLL "*class_2*"

Wyeksportowana Klasa pochodzi z klasy, która nie została wyeksportowana.

Aby zminimalizować prawdopodobieństwo uszkodzenia danych podczas eksportowania klasy z [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), upewnij się, że:

- Do wszystkich danych statycznych uzyskuje się dostęp za pośrednictwem funkcji wyeksportowanych z biblioteki DLL.

- Żadna z nieliniowych metod klasy nie może modyfikować danych statycznych.

- Żadna z nieliniowych metod klasy używa funkcji CRT lub innych funkcji biblioteki, które używają danych statycznych.

- W funkcjach klasy wbudowanej nie są używane funkcje CRT ani inne funkcje biblioteki, w których uzyskuje się dostęp do danych statycznych.

- Żadna metoda klasy (bez względu na dekreślenie) może używać typów, w których wystąpienie w EXE i DLL ma różnice danych statycznych.

Można uniknąć eksportowania klas przez zdefiniowanie biblioteki DLL, która definiuje klasę z funkcjami wirtualnymi, oraz funkcje, które można wywołać w celu utworzenia wystąpienia i usunięcia obiektów typu.  Następnie można wywołać funkcje wirtualne w typie.

C4275 można zignorować w wizualizacji C++ , jeśli pochodzą z typu w bibliotece C++ standardowej, kompilując wersję debug ( **/MTD**) i gdzie komunikat o błędzie kompilatora odnosi się do `_Container_base`.

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
