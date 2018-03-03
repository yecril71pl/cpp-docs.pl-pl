---
title: Odbicie (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fab5bb3c912aeea2598189965d424ba4508cf5c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reflection-ccli"></a>Odbicie (C++/CLI)
Odbicie umożliwia znanych typów poddanych w czasie wykonywania. Odbicie umożliwia wyliczanie typów danych w ramach danego zestawu, a członkami danego typu klasy lub wartości, które mogą być wykrywane. Dotyczy to niezależnie od tego, czy wiadomo lub odwołuje się do kompilacji typu. Dzięki temu odbicia przydatna funkcja dla rozwoju i narzędzia do zarządzania kodem.  
  
 Należy pamiętać, że podana nazwa zestawu jest silnej nazwy (zobacz [tworzenie i zestawy Using Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), która obejmuje zestaw w wersji, kultury i podpisywania informacji. Należy pamiętać, że nazwa przestrzeni nazw, w którym zdefiniowano typ danych można pobrać, wraz z nazwą klasy podstawowej.  
  
 Najczęściej dostęp do funkcji odbicia odbywa się za pośrednictwem <xref:System.Object.GetType%2A> metody. Ta metoda jest zapewniana przez [System::Object](https://msdn.microsoft.com/en-us/library/system.object.aspx), z którego pochodzi wszystkie klasy zbierane pamięci.  
  
 Odbicie w .exe skompilowanej za pomocą kompilatora Visual C++ jest dozwolone tylko, jeśli .exe jest zbudowany z **/CLR: pure** lub **/CLR: Safe** — opcje kompilatora. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015. Zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) Aby uzyskać więcej informacji.  
  
 Tematy w tej sekcji:  
  
-   [Instrukcje: implementacja architektury składnika plug-in przy użyciu odbicia (C++/CLI)](../dotnet/how-to-implement-a-plug-in-component-architecture-using-reflection-cpp-cli.md)  
  
-   [Instrukcje: wyliczanie typów danych w zestawach za pomocą odbicia (C++/CLI)](../dotnet/how-to-enumerate-data-types-in-assemblies-using-reflection-cpp-cli.md)  
  
 Aby uzyskać więcej informacji, zobacz [System.Reflection Namespace](https://msdn.microsoft.com/en-us/library/system.reflection.aspx)  
  
## <a name="example"></a>Przykład  
 `GetType` Metoda zwraca wskaźnik do <xref:System.Type> klasy obiektu, który opisuje typ, podczas gdy obiekt jest oparty. ( **Typu** obiekt nie zawiera żadnych informacji specyficznych dla wystąpienia.) Jeden taki element jest pełna nazwa typu, który może być wyświetlany w następujący sposób:  
  
 Należy pamiętać, że nazwa typu zawiera pełnego zakresu, w którym zdefiniowano typ, włącznie z przestrzenią nazw, i że jest wyświetlany w składni .NET z kropką jako operator rozpoznawania zakresów.  
  
```  
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
  
## <a name="example"></a>Przykład  
 Typy wartości mogą być używane z `GetType` również działać, ale musi zostać opakowany najpierw.  
  
```  
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
  
## <a name="example"></a>Przykład  
 Jak `GetType` metody [typeid](../windows/typeid-cpp-component-extensions.md) operator zwraca wskaźnik do **typu** obiektu, dlatego ten kod wskazuje nazwę typu **System.Int32**. Wyświetlanie nazwy typów jest najbardziej podstawową funkcją odbicia, ale jest technika potencjalnie bardziej użyteczne inspekcja lub odnajdywanie prawidłowe wartości dla typów wyliczenia. Można to zrobić za pomocą statycznych **Enum::GetNames** funkcji, która zwraca tablicę ciągów, każda z nich zawiera wartość wyliczenia w postaci tekstu.  Poniższy przykład pobiera tablicę ciągów, które opisano wartości wyliczenia wartości **opcje** wyliczenia (CLR) i wyświetla je w pętli.  
  
 Jeśli opcja czwarty jest dodawany do **opcje** wyliczenia, ten kod będzie zgłaszać nową opcję bez ponownej kompilacji, nawet jeśli wyliczenia jest zdefiniowany w osobny zestaw.  
  
```  
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
  
## <a name="example"></a>Przykład  
 `GetType` Obiektu obsługuje wiele elementów członkowskich i właściwości, których można użyć do sprawdzenia typu. Ten kod pobiera i przedstawia niektóre z tych informacji:  
  
```  
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
  
## <a name="example"></a>Przykład  
 Odbicie umożliwia także wyliczanie typów w zestawie i elementów członkowskich w klasach. Aby zademonstrować tę funkcję, zdefiniuj prostą klasę:  
  
```  
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
  
## <a name="example"></a>Przykład  
 Jeśli powyższy kod jest kompilowany do biblioteki DLL o nazwie vcpp_reflection_6.dll, następnie umożliwia odbicia sprawdzić zawartość tego zestawu. Obejmuje to przy użyciu odbicia statycznych funkcji API [Assembly::Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx) można załadować zestawu. Ta funkcja zwraca adres **zestawu** obiekt, który następnie można tworzyć zapytania dotyczące modułów i typów w ciągu.  
  
 Gdy system odbicia pomyślnie ładuje zestaw na tablicę **typu** obiekty są pobierane z [Assembly::GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx) funkcji. Każdy element tablicy zawiera informacje o jest innego typu, mimo że w takim przypadku tylko jedna klasa jest zdefiniowana. Przy użyciu pętli, każdy **typu** tej tablicy zapytanie o elementy członkowskie typu przy użyciu **Type::GetMembers** funkcji. Ta funkcja zwraca tablicę **MethodInfo** obiektów, każdy obiekt zawierający informacje o funkcji członkowskiej, element członkowski danych lub właściwości w typie.  
  
 Uwaga listy metod jawnie zawiera funkcje zdefiniowane w **TestClass** i funkcje niejawnie dziedziczone z **System::Object** klasy. W ramach są opisane w środowisku .NET, a nie w składni języka Visual C++ właściwości są wyświetlane jako podstawowy element członkowski danych używane przez funkcje get/set. Funkcje get/set są wyświetlane na liście jako prawidłowe metody. Odbicie jest obsługiwana przez środowisko uruchomieniowe języka wspólnego, nie za pomocą kompilatora Visual C++.  
  
 Chociaż ten kod jest używany do zbadania zestawu, który zdefiniowano, umożliwia także ten kod do zbadania zestawów platformy .NET. Na przykład jeśli zmienisz TestAssembly mscorlib, zostanie wyświetlona lista każdego typu i metody zdefiniowanej w pliku mscorlib.dll.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)