---
title: 'Instrukcje: Definiowanie oraz stosowanie wyliczeń w C++sposób niezamierzony'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 9787b7b96f83b2926c65209254c88eb56fe1a8ab
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774740"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Instrukcje: Definiowanie oraz stosowanie wyliczeń w C++sposób niezamierzony

W tym temacie omówiono typy wyliczeniowe w C++sposób niezamierzony.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Określanie typu podstawowego typu wyliczeniowego

Domyślnie jest podstawowym typem wyliczenia `int`.  Jednakże, można określić typu, który ma być podpisane lub niepodpisane rodzaje `int`, `short`, `long`, `__int32`, lub `__int64`.  Można również użyć `char`.

```
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

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Instrukcje konwertowanie między wyliczeniami zarządzanymi a standardowymi

Istnieje standardowa konwersja między wyliczeniem i typem całkowitym; Obsada jest wymagana.

```
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

Następujące operatory są prawidłowe dla typów wyliczeniowych w C++sposób niezamierzony:

|Operator|
|--------------|
|== != \< > \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operatory &#124; ^ & ~ ++ — są zdefiniowane tylko w przypadku wyliczenia z podstawowych typów, nie wliczając bool całkowitego.  Oba operandy muszą być typu wyliczenia.

Kompilator wykonuje nie statycznych lub dynamicznych sprawdzanie wyniku operacji wyliczenia. Operacja może spowodować wartość nie jest w zakresie prawidłowe moduły wyliczające wyliczenia.

> [!NOTE]
>  C ++ 11 wprowadza typy klas typu wyliczeniowego w niezarządzanym kodzie, które różnią się znacznie od klas wyliczenie zarządzane w C++sposób niezamierzony. W szczególności, typ klasy C ++ 11 wyliczenia nie obsługuje tego samego operatorów jako typ klasy wyliczenie zarządzane w C++sposób niezamierzony, i C++/kod źródłowy interfejsu wiersza polecenia należy podać specyfikator ułatwień dostępu w typie wyliczeniowym zarządzanych deklaracje klas, aby odróżnić je od niezarządzane (C ++ 11) deklaracje klas typu wyliczeniowego. Aby uzyskać więcej informacji na temat Wylicz klasy w C++sposób niezamierzony, C++/CX i C ++ 11, see [klasa wyliczeniowa](../extensions/enum-class-cpp-component-extensions.md).

```
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

```
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
