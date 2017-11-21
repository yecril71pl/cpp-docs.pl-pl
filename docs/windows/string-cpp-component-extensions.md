---
title: "Ciąg (C++ Component Extensions) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3fb87578a0046a70da9a68ab6a1a08b2d6a9f4d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="string--c-component-extensions"></a>Ciąg (C++ Component Extensions)
Obsługa kompilatora Visual C++ *ciągów*, które są obiekty reprezentujące tekst sekwencję znaków. Visual C++ obsługuje zmiennych ciągu, którego wartość jest niejawnie, i literały, którego wartość jest jawne ciągu w cudzysłowie.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Środowisko wykonawcze systemu Windows i środowisko uruchomieniowe języka wspólnego reprezentują ciągi jako obiekty, których alokacji pamięci odbywa się automatycznie. Oznacza to, że nie są wymagane jawnie odrzucić pamięci ciągu podczas kończenia umieszczane zmiennej ciągu poza zakresem lub aplikacji. Wskazuje, że okres istnienia obiektu ciągu jest mają być automatycznie zarządzane, należy zadeklarować typ ciągu z [uchwyt do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) modyfikator.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Architektura środowiska wykonawczego systemu Windows wymaga Visual C++ do zaimplementowania `String` typów danych w `Platform` przestrzeni nazw. Dla wygody udostępnia również Visual C++ `string` typ danych, który jest synonimem `Platform::String`w `default` przestrzeni nazw.  
  
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
 Aby uzyskać dodatkowe informacje i przykłady dotyczące ciągów, zobacz [Platform::String, std::wstring i literały (platformy)](http://msdn.microsoft.com/en-us/ec92fbc6-edf3-4137-a85e-8e29bdb857a8)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 W tym temacie omówiono sposób kompilatora Visual C++ przetwarza literałów ciągów uruchamianych przy użyciu **/CLR** — opcja kompilatora. Aby użyć **/CLR**, należy również użyć środowisko uruchomieniowe języka wspólnego (CLR), C + +/ CLI składni i zarządzane obiekty. Aby uzyskać więcej informacji na temat **/CLR**, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Podczas kompilowania za pomocą **/CLR**, kompilator przekonwertuje literały ciągów typu <xref:System.String>. Aby zachować zgodność z poprzednimi wersjami z istniejącego kodu są dwa wyjątki to:  
  
-   Obsługa wyjątków. Gdy literał ciągu jest zgłaszany, kompilator będzie przechwytywać go jako literału ciągu.  
  
-   Wnioskowanie szablonu. Gdy literał ciągu jest przekazywany jako argument szablonu, kompilator nie przekonwertuje go do <xref:System.String>. Uwaga: literały ciągu przekazany jako argument rodzajowy zostanie podwyższony do <xref:System.String>.  
  
 Kompilator ma także wbudowaną obsługę trzy operatory, które można zmienić, aby dostosować zachowanie przy ich:  
  
-   System::String ^ — operator + (System::String, System::String);  
  
-   System::String ^ — operator + (System::Object, System::String);  
  
-   System::String ^ — operator + (System::String, System::Object);  
  
 Po upływie <xref:System.String>, kompilator pole, jeśli to konieczne, a następnie połącz obiekt (z ToString) z ciągiem.  
  
> [!NOTE]
>  Daszek ("^") oznacza, że zadeklarowana zmienna dojścia do C + +/ CLI zarządzanego obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje łączenie i porównywanie ciągów.  
  
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
  
 **Dane wyjściowe**  
  
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
  
 **Przykład**  
  
 Poniższy przykład pokazuje, że można przeciążać operatory podane do kompilatora i znaleźć kompilatora przeciążenie funkcji, na podstawie <xref:System.String> typu.  
  
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
  
 **Dane wyjściowe**  
  
```Output  
overloaded +(String ^ a, String ^ b)   
  
overloaded +(String ^ a, Object ^ b)   
  
overloaded +(Object ^ a, String ^ b)   
  
String ^ a  
  
const char * a  
```  
  
 **Przykład**  
  
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
  
 **Dane wyjściowe**  
  
```Output  
char *  
  
String^ str  
  
System.SByte*  
  
System.String  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)   
 [Literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md)   
 [/ CLR (kompilacja języka wspólnego środowiska wykonawczego)](../build/reference/clr-common-language-runtime-compilation.md)