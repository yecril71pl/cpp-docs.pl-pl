---
title: Ciąg (C++/CLI i C++/CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: b9da900ffbfff34dc596d8981095d8285bf37208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171947"
---
# <a name="string--ccli-and-ccx"></a>Ciąg (C++/CLI i C++/CX)

Środowisko wykonawcze systemu Windows i środowisko uruchomieniowe języka wspólnego reprezentuje ciągi jako obiekty, których przydzieloną pamięć jest zarządzana automatycznie. Oznacza to, że nie jest wymagane jawne odrzucanie pamięci ciągu, gdy zmienna ciągu wykracza poza zakres lub że aplikacja zostanie zakończona. Aby wskazać, że okres istnienia obiektu ciągu ma być zarządzany automatycznie, zadeklaruj typ ciągu z modyfikatorem [dojście do obiektu (^)](handle-to-object-operator-hat-cpp-component-extensions.md) .

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Architektura środowisko wykonawcze systemu Windows wymaga, aby typ danych `String` znajdował się w przestrzeni nazw `Platform`. Dla wygody wizualizacji C++ udostępnia również typ danych `string`, który jest synonimem dla `Platform::String`, w przestrzeni nazw `default`.

### <a name="syntax"></a>Składnia

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Podczas kompilowania z `/clr`kompilator konwertuje literały ciągu na ciągi typu <xref:System.String>. Aby zachować zgodność z poprzednimi wersjami z istniejącym kodem, istnieją dwa wyjątki:

- Obsługa wyjątków. Gdy generowany jest literał ciągu, kompilator przechwytuje go jako literał ciągu.

- Odliczanie szablonu. Gdy literał ciągu jest przenoszona jako argument szablonu, kompilator nie przekonwertuje go na <xref:System.String>. Zauważ, że literały ciągu przesyłane jako argument generyczne zostaną podwyższenie poziomu do <xref:System.String>.

Kompilator ma także wbudowaną obsługę trzech operatorów, które można przesłonić w celu dostosowania ich zachowania:

- System:: String ^ operator + (system:: String, system:: String);

- System:: String ^ operator + (system:: Object, system:: String);

- System:: String ^ operator + (system:: String, system:: Object);

Gdy przeszedł <xref:System.String>, kompilator będzie Box, w razie potrzeby, a następnie łączy obiekt (z ToString) z ciągiem.

> [!NOTE]
> Daszek ("^") wskazuje, że zadeklarowana zmienna jest dojściem C++do obiektu zarządzanego/CLI.

Aby uzyskać więcej informacji, zobacz [literały ciągów i znaków](../cpp/string-and-character-literals-cpp.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/CLR**

### <a name="examples"></a>Przykłady

Poniższy przykład kodu ilustruje łączenie i Porównywanie ciągów.

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   // variables of System::String returning a System::String
   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   // accessing a character in the string
   Console::WriteLine(a[2]);

   // concatenation of three System::Strings
   Console::WriteLine(a + b + c);

   // concatenation of a System::String and string literal
   Console::WriteLine(a + "zzz");

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
   if (n == nullptr)
      Console::WriteLine("n is empty");
}
```

```Output
abcdef

abcghi

ghiabc

c

abcdefghi

abczzz

abc1

abc97

abc3.1

abcdef

a and b are equal

a and b are not equal

abc

n is empty
```

Poniższy przykład pokazuje, że można przeciążać operatory dostarczone przez kompilator i że kompilator znajdzie Przeciążenie funkcji na podstawie typu <xref:System.String>.

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

Poniższy przykład pokazuje, że kompilator rozróżnia ciągi natywne i ciągi <xref:System.String>.

```cpp
// string_operators_3.cpp
// compile with: /clr
using namespace System;
int func() {
   throw "simple string";   // const char *
};

int func2() {
   throw "string" + "string";   // returns System::String
};

template<typename T>
void func3(T t) {
   Console::WriteLine(T::typeid);
}

int main() {
   try {
      func();
   }
   catch(char * e) {
      Console::WriteLine("char *");
   }

   try {
      func2();
   }
   catch(String^ str) {
      Console::WriteLine("String^ str");
   }

   func3("string");   // const char *
   func3("string" + "string");   // returns System::String
}
```

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)<br/>
[Literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)
