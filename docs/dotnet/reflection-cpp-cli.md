---
title: Odbicie (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
ms.openlocfilehash: a17910e0288b81723aa837ba9204bb40713d5d49
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770817"
---
# <a name="reflection-ccli"></a>Odbicie (C++/CLI)

Odbicie umożliwia znanych danych typy poddanych w czasie wykonywania. Odbicie umożliwia wyliczanie typów danych w danym zestawie i elementy członkowskie typu danej klasy lub wartości, które mogą być wykrywane. Ta zasada obowiązuje niezależnie od tego, czy typ został znane lub odwołania w czasie kompilacji. To sprawia, że odbicie to przydatne dla rozwoju i narzędzia do zarządzania kodem.

Należy pamiętać, że podana nazwa zestawu silną nazwę (zobacz [tworzenie i zestawy Using Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), która obejmuje wersję zestawu, kultura i informacje o podpisywaniu. Należy zauważyć, że nazwa przestrzeni nazw, w którym zdefiniowano typ danych mogą być pobierane, wraz z nazwą klasy bazowej.

Najczęstszym sposobem uzyskania dostępu do funkcji odbicie jest za pośrednictwem <xref:System.Object.GetType%2A> metody. Ta metoda jest dostarczany przez <xref:System.Object?displayProperty=nameWithType>, z której pochodzą wszystkie klasy zebranych elementów bezużytecznych.

> [!NOTE]
> Rozważania na temat .exe utworzonych za pomocą kompilatora języka Visual C++ jest dozwolone tylko, jeśli .exe został utworzony za pomocą **/CLR: pure** lub **/CLR: Safe** opcje kompilatora. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i niedostępne w programie Visual Studio 2017. Zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji zobacz <xref:System.Reflection>

## <a name="example-gettype"></a>Przykład: GetType

`GetType` Metoda zwraca wskaźnik do <xref:System.Type> klasy obiektu, który opisuje typ, podczas gdy obiekt jest oparty. ( **Typu** obiekt nie zawiera żadnych informacji specyficznych dla danego wystąpienia.) Jeden taki element jest pełna nazwa typu, który może być wyświetlany w następujący sposób:

Należy pamiętać, że nazwa typu zawiera pełnego zakresu, w którym zdefiniowano typ, włącznie z przestrzenią nazw, i że jest wyświetlana w składni .NET z dot jako operatora rozpoznawania zakresu.

```cpp
// vcpp_reflection.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^ s = "sample string";
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());
}
```

```Output
full type name of 'sample string' is 'System.String'
```

## <a name="example-boxed-value-types"></a>Przykład: spakowane typy wartości

Typy wartości mogą być używane z `GetType` również działać, ale musi zostać opakowany najpierw.

```cpp
// vcpp_reflection_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Int32 i = 100;
   Object ^ o = i;
   Console::WriteLine("type of i = '{0}'", o->GetType());
}
```

```Output
type of i = 'System.Int32'
```

## <a name="example-typeid"></a>Przykład: typeid

Podobnie jak w przypadku `GetType` metody [typeid](../extensions/typeid-cpp-component-extensions.md) operator zwraca wskaźnik do **typu** obiektu, dlatego ten kod wskazuje nazwę typu **System.Int32**. Wyświetlanie nazwy typu jest najbardziej podstawowa funkcja odbicia, ale potencjalnie bardziej przydatną techniką jest sprawdzić lub odnajdywanie prawidłowe wartości dla typów wyliczeniowych. Można to zrobić przy użyciu statycznej **Enum::GetNames** funkcja, która zwraca tablicę ciągów, każdy z nich zawierający wartości wyliczenia w postaci tekstu.  Poniższy przykład pobiera tablicę ciągów, które opisano w wartości wyliczenia wartości **opcje** wyliczenia (CLR) i wyświetla je w pętli.

Jeśli dostępny czwarty etap jest dodawany do **opcje** wyliczenia, ten kod będzie zgłaszać nowa opcja bez ponownej kompilacji, nawet jeśli nie zdefiniowano wyliczenia w osobnym zestawie.

```cpp
// vcpp_reflection_3.cpp
// compile with: /clr
using namespace System;

enum class Options {   // not a native enum
   Option1, Option2, Option3
};

int main() {
   array<String^>^ names = Enum::GetNames(Options::typeid);

   Console::WriteLine("there are {0} options in enum '{1}'",
               names->Length, Options::typeid);

   for (int i = 0 ; i < names->Length ; i++)
      Console::WriteLine("{0}: {1}", i, names[i]);

   Options o = Options::Option2;
   Console::WriteLine("value of 'o' is {0}", o);
}
```

```Output
there are 3 options in enum 'Options'
0: Option1
1: Option2
2: Option3
value of 'o' is Option2
```

## <a name="example-gettype-members-and-properties"></a>Przykład: Właściwości i elementy członkowskie GetType

`GetType` Obiekt obsługuje szereg elementów członkowskich i właściwości, których można użyć do sprawdzenia typu. Ten kod pobiera i wyświetla niektóre z tych informacji:

```cpp
// vcpp_reflection_4.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine("type information for 'String':");
   Type ^ t = String::typeid;

   String ^ assemblyName = t->Assembly->FullName;
   Console::WriteLine("assembly name: {0}", assemblyName);

   String ^ nameSpace = t->Namespace;
   Console::WriteLine("namespace: {0}", nameSpace);

   String ^ baseType = t->BaseType->FullName;
   Console::WriteLine("base type: {0}", baseType);

   bool isArray = t->IsArray;
   Console::WriteLine("is array: {0}", isArray);

   bool isClass = t->IsClass;
   Console::WriteLine("is class: {0}", isClass);
}
```

```Output
type information for 'String':
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral,
PublicKeyToken=b77a5c561934e089
namespace: System
base type: System.Object
is array: False
is class: True
```

## <a name="example-enumeration-of-types"></a>Przykład: Wyliczanie typów

Odbicie umożliwia także wyliczanie typów w zestawie i członków w ramach klasy. Aby zademonstrować tę funkcję, należy zdefiniować prostą klasę:

```cpp
// vcpp_reflection_5.cpp
// compile with: /clr /LD
using namespace System;
public ref class TestClass {
   int m_i;
public:
   TestClass() {}
   void SimpleTestMember1() {}
   String ^ SimpleMember2(String ^ s) { return s; }
   int TestMember(int i) { return i; }
   property int Member {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }
};
```

## <a name="example-inspection-of-assemblies"></a>Przykład: inspekcja zestawów

Jeśli powyższy kod jest kompilowany do biblioteki DLL o nazwie vcpp_reflection_6.dll, można następnie używać odbicia, aby sprawdzić zawartość tego zestawu. Obejmuje to przy użyciu odbicia statyczne xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType funkcji interfejsu API można załadować zestawu. Ta funkcja zwróci adres **zestawu** obiektu, który następnie może być odpytywany modułów i typów w ramach informacje.

Gdy system odbicia pomyślnie ładuje zestaw tablicę **typu** obiektów jest pobierany za pomocą <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> funkcji. Każdy element tablicy informacjami o innego typu, mimo że w tym przypadku tylko jedna klasa jest zdefiniowana. Za pomocą pętli, każdy **typu** w tej tablicy jest wysyłane zapytanie o elementy członkowskie typu przy użyciu **Type::GetMembers** funkcji. Ta funkcja zwraca tablicę **MethodInfo** obiektów, każdy obiekt zawierający informacje o funkcji elementu członkowskiego, element członkowski danych lub właściwości w typie.

Uwaga lista metod jawnie obejmuje funkcje zdefiniowane w **TestClass** i funkcji niejawnie dziedziczone z **System::Object** klasy. W ramach opisywanego na platformie .NET, a nie przy użyciu składni języka Visual C++ właściwości są wyświetlane jako podstawowy element członkowski danych uzyskiwał dostęp do funkcji get/set. Funkcje get/set są wyświetlane na tej liście jako metody regularnego. Odbicie jest obsługiwany przez środowisko uruchomieniowe języka wspólnego, nie przez kompilator języka Visual C++.

Mimo że ten kod jest używany do inspekcji zestawu, który został zdefiniowany, umożliwia także ten kod do inspekcji zestawy .NET. Na przykład jeśli zmienisz TestAssembly do mscorlib, następnie zobaczysz listę każdego typu i metody zdefiniowanej w mscorlib.dll.

```cpp
// vcpp_reflection_6.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;
using namespace System::Reflection;
int main() {
   Assembly ^ a = nullptr;
   try {
      // load assembly -- do not use file extension
      // will look for .dll extension first
      // then .exe with the filename
      a = Assembly::Load("vcpp_reflection_5");
   }
   catch (FileNotFoundException ^ e) {
      Console::WriteLine(e->Message);
      return -1;
   }

   Console::WriteLine("assembly info:");
   Console::WriteLine(a->FullName);
   array<Type^>^ typeArray = a->GetTypes();

   Console::WriteLine("type info ({0} types):", typeArray->Length);

   int totalTypes = 0;
   int totalMembers = 0;
   for (int i = 0 ; i < typeArray->Length ; i++) {
      // retrieve array of member descriptions
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();

      Console::WriteLine("  members of {0} ({1} members):",
      typeArray[i]->FullName, member->Length);
      for (int j = 0 ; j < member->Length ; j++) {
         Console::Write("       ({0})",
         member[j]->MemberType.ToString() );
         Console::Write("{0}  ", member[j]);
         Console::WriteLine("");
         totalMembers++;
      }
      totalTypes++;
   }
   Console::WriteLine("{0} total types, {1} total members",
   totalTypes, totalMembers);
}
```

## <a name="implement"></a> Jak: Implementacja architektury składnika Plug-In przy użyciu odbicia

Poniższe przykłady kodu ilustrują użycie odbicia do implementowania prostego architektury "wtyczki". Pierwszy listy jest aplikacją, a drugi ma wtyczce. Aplikacja jest wiele formularza dokumentu, która wypełnia się przy użyciu klas na podstawie formularza w biblioteki DLL dodatku plug-in dostarczana jako argument wiersza polecenia.

Aplikacja próbuje załadować zestaw podany przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> metody. Jeśli operacja się powiedzie, typy w zestawie są wyliczane przy użyciu <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> metody. Każdy typ są następnie sprawdzane pod kątem zgodności za pomocą <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> metody. W tym przykładzie klasach znalezionych w zestawie podana, musi pochodzić od <xref:System.Windows.Forms.Form> klasy, aby kwalifikować się jako dodatku typu plug-in.

Zgodne klasy następnie są tworzone za pomocą <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> metody, która akceptuje <xref:System.Type> jako argument i zwraca wskaźnik do nowego wystąpienia. Każde nowe wystąpienie jest następnie dołączony do formularza i wyświetlane.

Należy pamiętać, że <xref:System.Reflection.Assembly.Load%2A> metoda akceptuje nazwy zestawów, zawierające rozszerzenie pliku. Funkcji main w aplikacji przycina wszystkie podane rozszerzenia, więc poniższy kod działa w obu przypadkach.

### <a name="example"></a>Przykład

Poniższy kod definiuje aplikację, która akceptuje wtyczek. Jako pierwszy argument musi być podana nazwa zestawu. Ten zestaw może zawierać co najmniej jedną publiczną <xref:System.Windows.Forms.Form> typu pochodnego.

```cpp
// plugin_application.cpp
// compile with: /clr /c
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;

ref class PluggableForm : public Form  {
public:
   PluggableForm() {}
   PluggableForm(Assembly^ plugAssembly) {
      Text = "plug-in example";
      Size = Drawing::Size(400, 400);
      IsMdiContainer = true;

      array<Type^>^ types = plugAssembly->GetTypes( );
      Type^ formType = Form::typeid;

      for (int i = 0 ; i < types->Length ; i++) {
         if (formType->IsAssignableFrom(types[i])) {
            // Create an instance given the type description.
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));
            if (f) {
               f->Text = types[i]->ToString();
               f->MdiParent = this;
               f->Show();
            }
         }
      }
   }
};

int main() {
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");
   Application::Run(gcnew PluggableForm(a));
}
```

### <a name="example"></a>Przykład

Poniższy kod definiuje trzy klasy pochodne <xref:System.Windows.Forms.Form>. Jeśli nazwa wynikowa Nazwa zestawu jest przekazywany do pliku wykonywalnego na poprzedniej liście, każda z tych trzech klas będą wykrywane i wystąpienia, pomimo faktu, że były wszystkie nieznane do hostowania aplikacji w czasie kompilacji.

```cpp
// plugin_assembly.cpp
// compile with: /clr /LD
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;
using namespace System::Drawing;

public ref class BlueForm : public Form {
public:
   BlueForm() {
      BackColor = Color::Blue;
   }
};

public ref class CircleForm : public Form {
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);
   }
};

public ref class StarburstForm : public Form {
public:
   StarburstForm(){
      BackColor = Color::Black;
   }
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      Pen^ p = gcnew Pen(Color::Red, 2);
      Random^ r = gcnew Random( );
      Int32 w = ClientSize.Width;
      Int32 h = ClientSize.Height;
      for (int i=0; i<100; i++) {
         float x1 = w / 2;
         float y1 = h / 2;
         float x2 = r->Next(w);
         float y2 = r->Next(h);
         args->Graphics->DrawLine(p, x1, y1, x2, y2);
      }
   }
};
```

## <a name="enumerate"></a> Jak: Wyliczanie typów danych w zestawach za pomocą odbicia

Poniższy przykład demonstruje wyliczanie typów publicznych i elementów członkowskich przy użyciu <xref:System.Reflection>.

Podana nazwa zestawu, w katalogu lokalnym lub w pamięci podręcznej GAC, poniższy kod próbuje otworzyć zestaw i pobrać opisy. Jeśli to się powiedzie, każdy typ jest wyświetlany z jego publiczne elementy członkowskie.

Należy pamiętać, że <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> wymaga, że jest używana bez rozszerzenia pliku. W związku z tym za pomocą "mscorlib.dll" jako argumentu wiersza polecenia zakończy się niepowodzeniem, gdy za pomocą tylko "mscorlib" spowoduje wyświetlanie typów programu .NET Framework. Jeśli nazwa zestawu nie zostanie podany, kod wykryje i zgłaszać typów w bieżącym zestawie (EXE, wynikające z tego kodu).

### <a name="example"></a>Przykład

```cpp
// self_reflection.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;
using namespace System::Collections;

public ref class ExampleType {
public:
   ExampleType() {}
   void Func() {}
};

int main() {
   String^ delimStr = " ";
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ args = Environment::CommandLine->Split( delimiter );

// replace "self_reflection.exe" with an assembly from either the local
// directory or the GAC
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");
   Console::WriteLine(a);

   int count = 0;
   array<Type^>^ types = a->GetTypes();
   IEnumerator^ typeIter = types->GetEnumerator();

   while ( typeIter->MoveNext() ) {
      Type^ t = dynamic_cast<Type^>(typeIter->Current);
      Console::WriteLine("   {0}", t->ToString());

      array<MemberInfo^>^ members = t->GetMembers();
      IEnumerator^ memberIter = members->GetEnumerator();
      while ( memberIter->MoveNext() ) {
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);
         Console::Write("      {0}", mi->ToString( ) );
         if (mi->MemberType == MemberTypes::Constructor)
            Console::Write("   (constructor)");

         Console::WriteLine();
      }
      count++;
   }
   Console::WriteLine("{0} types found", count);
}
```

## <a name="see-also"></a>Zobacz także

- [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
