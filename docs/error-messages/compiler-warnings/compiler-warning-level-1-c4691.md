---
title: Ostrzeżenie kompilatora (poziom 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 6a4d1de621983794acfae4de7707ba127df9a1b7
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685570"
---
# <a name="compiler-warning-level-1-c4691"></a>Ostrzeżenie kompilatora (poziom 1) C4691

"Type": Oczekiwano typu odwołania w nieużywanym zestawie "File", w zamian użyto typu zdefiniowanego w bieżącej jednostce tłumaczenia

Nie można odwołać się do pliku metadanych zawierającego pierwotną definicję typu, a kompilator używa definicji typu lokalnego.

W przypadku ponownego kompilowania *pliku*C4691 można zignorować lub wyłączyć za pomocą [ostrzeżenia](../../preprocessor/warning.md)pragma.  Oznacza to, że jeśli tworzony plik jest taki sam jak plik, którego kompilator oczekuje na znalezienie definicji typu, można zignorować C4691.

Jednak nieoczekiwane zachowanie może wystąpić, jeśli kompilator używa definicji, która nie jest z tego samego zestawu, do którego odwołuje się metadane; Typy CLR są wpisywane nie tylko nazwami typu, ale również przez zestaw.  Oznacza to, że typ Z z zestawu z.dll różni się od typu z y.dll zestawu.

## <a name="examples"></a>Przykłady

Ten przykład zawiera pierwotną definicję typu.

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

Ten przykład odwołuje się C4691_a.dll i deklaruje pole typu Original_Type.

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

Poniższy przykład generuje C4691.  Zwróć uwagę, że ten przykład zawiera definicję Original_Type i nie odwołuje się do C4691a.dll.

Aby rozwiązać ten problem, należy odwołać się do pliku metadanych, który zawiera pierwotną definicję typu, i usunąć lokalną deklarację i definicję.

```cpp
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```
