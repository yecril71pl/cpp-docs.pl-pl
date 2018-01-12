---
title: "Kompilatora (poziom 4) ostrzeżenie C4471 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4471
dev_langs: C++
helpviewer_keywords: C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e7429a458c90c30fdf57b985cda88ca85c6d29c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4471"></a>Kompilator C4471 ostrzegawcze (poziom 4)
"*wyliczenie*": deklaracja przekazująca dalej wyliczenie niebędące w zakresie musi być typu podstawowego (założono typ int)  
  
Deklaracja przekazująca dalej wyliczenie niebędące w zakresie odnaleziono bez specyfikatora typu podstawowego. Domyślnie zakłada Visual C++ `int` jest typem podstawowym dla wyliczenia. Jeśli innego typu jest używana w definicja wyliczenia, na przykład, jeśli określono innego typu explicit, lub innego typu jest niejawnie ustawiona przez inicjatora mogą powodować problemy. Możesz mieć problemy związane z przenośnością; inne kompilatory zakłada się `int` jest podstawowym typem wyliczenia.  
  
To ostrzeżenie jest wyłączone domyślnie; można użyć/Wall lub /w*N*4471, aby ją włączyć w wierszu polecenia, lub użyj #pragma [ostrzeżenie](../../preprocessor/warning.md) w pliku źródłowym.  
  
W niektórych przypadkach to ostrzeżenie jest fałszywe. Jeśli deklaracja przekazująca dalej wyliczania pojawia się po definicji, mogą wyzwalać to ostrzeżenie. Na przykład ten kod jest prawidłowy, chociaż może to spowodować C4471:  
  
```cpp  
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```  
  
## <a name="example"></a>Przykład  
Ogólnie rzecz biorąc jest bezpieczne, użyj pełnej definicji dla zamiast deklaracja przekazująca dalej wyliczenie niebędące w zakresie. Można umieścić definicję w pliku nagłówka i dołączyć go w plikach źródłowych, które odwołują się do niego. To działanie jest kod napisany w języku C ++ 98 i później. Zalecamy to rozwiązanie dla przenośność i łatwości konserwacji.  
  
```cpp  
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```  
  
## <a name="example"></a>Przykład  
W języku C ++ 11 można dodać jawnego typu wyliczenia niewystępującego w zakresie i jego deklaracja przekazująca dalej. Zalecamy to rozwiązanie tylko wtedy, gdy logiki włączenia nagłówka złożonych uniemożliwia korzystanie z definicji zamiast deklaracja przekazująca dalej. To rozwiązanie może prowadzić do konserwacyjne: Zmień typ podstawowy używany do definicji wyliczenia, należy również zmienić wszystkie deklaracje do przodu, aby dopasować, czy masz dyskretnej błędów w kodzie. Deklaracja przekazująca dalej można umieścić w pliku nagłówka, aby zminimalizować ten problem.  
  
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
  
Jeśli określisz jawnego typu wyliczania, zalecamy również włączyć ostrzeżenie [C4369](compiler-warning-level-1-C4369.md), który jest domyślnie włączone. Identyfikuje przypadków, gdy element wyliczenia wymaga innego typu niż jawnie określonego typu.
  
## <a name="example"></a>Przykład  
Można zmienić kod, aby używał zakresami wyliczenia, funkcja, która jest nowego w języku C ++ 11. Należy zmienić definicję i kodu klienta, który korzysta z typu wyliczeniowego do użycia w zakresie wyliczenia. Firma Microsoft zaleca się, że używasz zakresami wyliczenia w przypadku wystąpienia problemów z zanieczyszczeniu przestrzeń nazw jako nazwy elementów wyliczenia zdefiniowanych są ograniczone do zakresu wyliczenia. Inna funkcja o zakresie wyliczenia jest jej elementów członkowskich nie można niejawnie przekonwertować typu całkowitego lub wyliczenia typu, który może być źródłem subtelnych błędów.

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
  
