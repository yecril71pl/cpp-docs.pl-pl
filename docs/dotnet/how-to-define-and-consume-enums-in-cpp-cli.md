---
title: 'Instrukcje: Definiowanie wyliczeń w języku C++/interfejsie wiersza polecenia i korzystanie z nich'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: f09bb6e9fac30b72c3c4e0682c3d90f2ea9f8760
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216417"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Instrukcje: Definiowanie wyliczeń w języku C++/interfejsie wiersza polecenia i korzystanie z nich

W tym temacie omówiono wyliczenia w języku C++/CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Określanie typu podstawowego wyliczenia

Domyślnie typem podstawowym wyliczenia jest **`int`** .  Można jednak określić typ, który ma być podpisany lub niepodpisany formy **`int`** , **`short`** ,, **`long`** **`__int32`** lub **`__int64`** .  Można również użyć **`char`** .

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

**Dane wyjściowe**

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

**Dane wyjściowe**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operatory i wyliczenia

Następujące operatory są prawidłowe dla typów wyliczeniowych w języku C++/CLI:

|Operator|
|--------------|
|== != \< >\<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operatory &#124; ^ & ~ + +--są zdefiniowane tylko dla wyliczeń z typami podstawowymi, bez uwzględniania wartości bool.  Oba operandy muszą być typu wyliczeniowego.

Kompilator nie sprawdza statycznego ani dynamicznego sprawdzenia wyniku operacji enum; Operacja może spowodować, że wartość nie należy do zakresu prawidłowych modułów wyliczających wyliczenia.

> [!NOTE]
> W języku c++ 11 wprowadzono typy klas enum w niezarządzanym kodzie, które znacząco różnią się od zarządzanych klas wyliczeniowych w języku C++/CLI. W szczególności typ klasy wyliczeniowej języka C++ 11 nie obsługuje tych samych operatorów co typ zarządzanej klasy wyliczeniowej w języku C++/CLI, a kod źródłowy języka C++/CLI musi udostępniać specyfikator dostępności w deklaracjach klasy zarządzanej wyliczenia w celu odróżnienia ich od niezarządzanych (C++ 11) deklaracji klasy wyliczeniowej. Aby uzyskać więcej informacji na temat klas wyliczenia w języku C++/CLI, C++/CX i C++ 11, zobacz [enum Class](../extensions/enum-class-cpp-component-extensions.md).

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

**Dane wyjściowe**

```Output
4
1
True
```

## <a name="see-also"></a>Zobacz także

[enum, klasa](../extensions/enum-class-cpp-component-extensions.md)
