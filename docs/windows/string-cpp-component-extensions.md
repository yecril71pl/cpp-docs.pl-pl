---
title: Ciąg (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6fd13c3e94f6b42bd485c645233f84272c6eae91
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194836"
---
# <a name="string--c-component-extensions"></a>Ciąg (C++ Component Extensions)

Obsługa kompilatora Visual C++ *ciągi*, które są obiektami, które reprezentują tekstu jako sekwencja znaków. Visual C++ obsługuje zmiennych ciągu, którego wartość jest niejawny, i wszystkie literały, którego wartością jest jawne ciągów w cudzysłowach.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Środowisko uruchomieniowe Windows i środowisko uruchomieniowe języka wspólnego reprezentuje ciągi jako obiekty, których ilość przydzielonej pamięci odbywa się automatycznie. Oznacza to nie należy jawnie odrzucić pamięci ciągu, po zakończeniu zacznie zmiennej ciągu poza zakres lub aplikacji. Aby wskazać, że okres istnienia obiektu ciągu ma odbywać się automatycznie, należy zadeklarować typ ciągu z [uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) modyfikator.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Architektura Windows Runtime wymaga Visual C++ do implementacji `String` typu danych w `Platform` przestrzeni nazw. Dla Twojej wygody Visual C++ są także `string` typ danych, który jest synonimem `Platform::String`w `default` przestrzeni nazw.

### <a name="syntax"></a>Składnia

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji i przykładów dotyczących parametrów, zobacz [Platform::String, std::wstring i literały (platformy)](https://msdn.microsoft.com/ec92fbc6-edf3-4137-a85e-8e29bdb857a8)

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

W tym temacie omówiono, jak kompilator języka Visual C++ przetwarza Literały ciągu, po uruchomieniu przy użyciu `/clr` — opcja kompilatora. Aby użyć `/clr`, należy również użyć środowisko uruchomieniowe języka wspólnego (CLR), C + +/ składnia interfejsu wiersza polecenia i obiektów zarządzanych. Aby uzyskać więcej informacji na temat `/clr`, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

Podczas kompilowania za pomocą `/clr`, kompilator przekonwertuje literałów ciągów typu <xref:System.String>. Aby zachować zgodność z poprzednimi wersjami z istniejącym kodem są dwa wyjątki od tej reguły:

- Obsługa wyjątków. Gdy literał ciągu jest zgłaszany, kompilator będzie przechwytywać je jako ciąg literału.

- Wnioskowanie szablonu. Gdy literał ciągu jest przekazywany jako argument szablonu, kompilator nie przekonwertuje go do <xref:System.String>. Uwaga: literały ciągu przekazany jako argument rodzajowy zostanie podniesiony do <xref:System.String>.

Kompilator również ma wbudowaną obsługę operatorów trzech, które można przesłonić, aby dostosować jego zachowanie:

- System::String ^ — operator + (System::String, System::String);

- System::String ^ — operator + (System::Object, System::String);

- System::String ^ — operator + (System::String, System::Object);

Przy przekazywaniu <xref:System.String>, kompilator będzie polu, jeśli to konieczne, a następnie połącz obiekt (z ToString) na ciąg.

> [!NOTE]
> Daszek ("^") wskazuje, że Zmienna zadeklarowana dojścia do C + +/ CLI zarządzanego obiektu.

Aby uzyskać więcej informacji, zobacz [literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora:   **/CLR**

### <a name="examples"></a>Przykłady

Poniższy przykład kodu demonstruje, łączenie i porównywanie ciągów.

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String ^ a = gcnew String("abc");
   String ^ b = "def";   // same as gcnew form
   Object ^ c = gcnew String("ghi");

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

   // you can append to a System::String ^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String ^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)  
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)  
      Console::WriteLine("a and b are not equal");

   // System:String ^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String ^
   String ^ n;
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

Poniższy przykład pokazuje, że można przeciążać operatory podane do kompilatora i czy kompilator znajdzie przeciążenia funkcji na podstawie <xref:System.String> typu.

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String ^ a) {
   Console::WriteLine("String ^ a");
}

// overload will be called instead of compiler defined operator
String ^ operator +(String ^ a, String ^ b) {
   return ("overloaded +(String ^ a, String ^ b)");
}

// overload will be called instead of compiler defined operator
String ^ operator +(Object ^ a, String ^ b) {
   return ("overloaded +(Object ^ a, String ^ b)");
}

// overload will be called instead of compiler defined operator
String ^ operator +(String ^ a, Object ^ b) {
   return ("overloaded +(String ^ a, Object ^ b)");
}

int main() {
   String ^ a = gcnew String("abc");
   String ^ b = "def";   // same as gcnew form
   Object ^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String ^ a, String ^ b)

overloaded +(String ^ a, Object ^ b)

overloaded +(Object ^ a, String ^ b)

String ^ a

const char * a
```

Poniższy przykład pokazuje, że kompilator rozróżnia ciągi natywne i <xref:System.String> ciągów.

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

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)  
[Literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md)  
[/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)