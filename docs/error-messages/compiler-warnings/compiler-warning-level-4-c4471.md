---
title: Kompilatora (poziom 4) ostrzeżenie C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 0345b730b8fc37329f632bb5d8486c67efd8e3b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400789"
---
# <a name="compiler-warning-level-4-c4471"></a>Kompilatora (poziom 4) ostrzeżenie C4471

"*wyliczenie*": deklaracja zapowiadająca wyliczenia nieobjętego zakresem musi mieć podstawowy typ (zakładany jest int)

Deklaracja zapowiadająca wyliczenia nieobjętego zakresem odnaleziono bez specyfikatora typu bazowego. Domyślnie przyjęto założenie, Visual C++ `int` jest podstawowym typem wyliczenia. Może to spowodować problemy, czy innego typu jest używana w definicji wyliczenia, na przykład, jeśli określono innego typu explicit, czy innego typu jest niejawnie ustawiony przez inicjatora. Może również mieć problemy; nie należy zakładać, inne kompilatory `int` jest podstawowym typem wyliczenia.

To ostrzeżenie jest wyłączone domyślnie; Możesz użyć /Wall lub Wn*N*4471, aby ją włączyć w wierszu polecenia lub użyj #pragma [ostrzeżenie](../../preprocessor/warning.md) w pliku źródłowym.

W niektórych przypadkach to ostrzeżenie jest fałszywe. Jeśli deklaracja wyliczenia pojawi się po definicji, może wyzwalać to ostrzeżenie. Na przykład ten kod jest prawidłowy, mimo że może to spowodować C4471:

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>Przykład

Ogólnie rzecz biorąc jest bezpieczny w użyciu pełna definicja wyliczenia niewystępującego w zakresie zamiast deklaracją do przodu. Możesz umieścić definicję w pliku nagłówkowym i uwzględnić go w plikach źródłowych, które odwołują się do niego. To działanie kodu napisanego w języku C ++ 98 i nowszych. Firma Microsoft zaleca to rozwiązanie do przenoszenia i łatwość konserwacji.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>Przykład

W języku C ++ 11 możesz dodać jawnego typu wyliczenia niewystępującego w zakresie i jej deklaracją do przodu. Firma Microsoft zaleca tego rozwiązania, tylko wtedy, gdy logika włączenia complex — nagłówek uniemożliwia korzystanie z definicji zamiast deklaracją do przodu. To rozwiązanie może prowadzić do konserwacyjne: Zmień typ podstawowy, używane w definicji wyliczenia, należy także zmienić wszystkie deklaracje przechodzenia do przodu do dopasowania, czy masz dyskretnej błędów w kodzie. Deklaracją do przodu można umieścić w pliku nagłówka, aby zminimalizować ten problem.

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

Jeśli określisz jawnego typu wyliczenia, firma Microsoft zaleca również włączyć ostrzeżenie [C4369](compiler-warning-level-1-C4369.md), która jest domyślnie włączone. Identyfikuje przypadki, w którym element wyliczenia wymaga innego typu niż jawnie określonego typu.

## <a name="example"></a>Przykład

Możesz zmienić swój kod, aby użyć wyliczeniowym w zakresie funkcji, co nowego w języku C ++ 11. Zarówno definicję, jak i wszelki kod klienta, który używa typu wyliczenia musi zostać zmieniona na typ wyliczeniowy w zakresie użycia. Zaleca się, że używasz wyliczeniowym, jeśli masz problemy z zanieczyszczenie przestrzeni nazw, nazw elementów zdefiniowanych wyliczenia są ograniczone do zakresu wyliczenia. Kolejną funkcją wyliczeń w zakresie jest jego składowych nie można niejawnie przekonwertować na inny typ całkowity lub wyliczeniowy, który może być źródłem subtelnych błędów.

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```

