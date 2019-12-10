---
title: 'Porady: definiowanie wyliczeń w języku C++/interfejsie wiersza polecenia i korzystanie z nich'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 68f8e113f6199d3b320bc6d241ee3396d2b70a1a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988224"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Porady: definiowanie wyliczeń w języku C++/interfejsie wiersza polecenia i korzystanie z nich

W tym temacie omówiono wyliczenia w C++/CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Określanie typu podstawowego wyliczenia

Domyślnie typem podstawowym wyliczenia jest `int`.  Można jednak określić typ, który ma być podpisany lub niepodpisany formularzy `int`, `short`, `long`, `__int32`lub `__int64`.  Możesz również użyć `char`.

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**Output**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Jak konwertować między wyliczeniami zarządzanymi i standardowymi

Nie istnieje standardowa konwersja między wyliczeniem a typem całkowitym; wymagane jest rzutowanie.

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**Output**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operatory i wyliczenia

Następujące operatory są prawidłowe w wyliczeniach w C++/CLI:

|Operator|
|--------------|
|== != \< > \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operatory &#124; ^ & ~ + +--są zdefiniowane tylko dla wyliczeń z typami podstawowymi całkowitymi, bez uwzględniania wartości bool.  Oba operandy muszą być typu wyliczeniowego.

Kompilator nie sprawdza statycznego ani dynamicznego sprawdzenia wyniku operacji enum; Operacja może spowodować, że wartość nie należy do zakresu prawidłowych modułów wyliczających wyliczenia.

> [!NOTE]
>  W języku c++ 11 wprowadzono typy klas wyliczenia w niezarządzanym kodzie, które są znacznie inne C++niż zarządzane klasy wyliczeniowe w/CLI. W szczególności typ klasy wyliczeniowej języka C++ 11 nie obsługuje tych samych operatorów co typ zarządzanej klasy wyliczeniowej w C++/CLI C++, a/CLI kod źródłowy musi udostępniać specyfikator dostępności w deklaracjach klasy zarządzanej wyliczenia w celu odróżnienia ich od niezarządzanych (c++ 11) deklaracji klasy wyliczeniowej. Aby uzyskać więcej informacji na temat klas C++wyliczenia w C++/CLI,/CX i c++ 11, zobacz [enum class](../extensions/enum-class-cpp-component-extensions.md).

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**Output**

```Output
4
1
True
```

## <a name="see-also"></a>Zobacz także

[enum class](../extensions/enum-class-cpp-component-extensions.md)
