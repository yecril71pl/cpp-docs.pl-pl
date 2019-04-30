---
title: Kompilator ostrzeżenie (poziom 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: c194e19c8766b67eb7deef32e7228564cda5f1e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406382"
---
# <a name="compiler-warning-level-1-c4691"></a>Kompilator ostrzeżenie (poziom 1) C4691

"type": oczekiwano typu odwołania w zestawie nieużywanej 'Plik' typ zdefiniowany w bieżącej jednostce tłumaczenia, zamiast tego użyć

Nie odwołuje się plik metadanych zawierający oryginalnej definicji typu, a kompilator używa definicję typu lokalnego.

W przypadku, gdy są ponownie skompilować *pliku*, mogą być ignorowane lub wyłączone z pragmą C4691 [ostrzeżenie](../../preprocessor/warning.md).  Oznacza to jeśli plik, który tworzysz jest taki sam jak plik, w których kompilator spodziewa się znaleźć definicję typu, możesz zignorować C4691.

Jednak może wystąpić nieoczekiwane zachowanie, jeśli kompilator używa definicję, która nie pochodzi z tego samego zestawu, który odwołuje się do metadanych; Typy CLR są wpisane, nie tylko przez nazwę typu, ale również przez zestaw.  Oznacza to z typem Z z zestawu z.dll różni się od typu Z z y.dll zestawu.

## <a name="example"></a>Przykład

W tym przykładzie zawiera oryginalnej definicji typu.

```
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono C4691_a.dll i deklaruje pole o typie Original_Type.

```
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4691.  Zwróć uwagę, w tym przykładzie zawiera definicję dla Original_Type i nie odwołuje się C4691a.dll.

Aby rozwiązać problem, Przywołaj plik metadanych zawierający oryginalnej definicji typu i usuwanie lokalnej deklaracji i definicji.

```
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