---
title: Typy zarządzane (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: b91918d526d83d4cf47436d02b7c67038576bafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152778"
---
# <a name="managed-types-ccli"></a>Typy zarządzane (C++/CLI)

Visual C++ umożliwia dostęp do funkcji platformy .NET za pomocą zarządzane typy, które zapewniają obsługę funkcji środowiska uruchomieniowego języka wspólnego i podlegają one zalety i ograniczenia środowiska uruchomieniowego.

## <a name="main_functions"></a> Typy zarządzane i funkcja main

Podczas pisania aplikacji za pomocą **/CLR**, argumenty **main()** funkcja nie może być typu zarządzanego.

Przykładem prawidłowego podpisu jest:

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="dotnet"></a> .NET framework odpowiedniki typów natywnych języka C++

W poniższej tabeli przedstawiono słowa kluczowe dla wbudowanych typów języka Visual C++, które są aliasy wstępnie zdefiniowanych typów w **systemu** przestrzeni nazw.

|Typ wizualizacji języka C++|Typ programu .NET Framework|
|-----------------------|-------------------------|
|**void**|<xref:System.Void?displayProperty=nameWithType>|
|**bool**|<xref:System.Boolean?displayProperty=nameWithType>|
|**podpisany char** |<xref:System.SByte?displayProperty=nameWithType>|
|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|
|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|
|**krótki** i **short ze znakiem**|<xref:System.Int16?displayProperty=nameWithType>|
|**short bez znaku**|<xref:System.UInt16?displayProperty=nameWithType>|
|**int**, **podpisany int**, **długie**, i **podpisany długo**|<xref:System.Int32?displayProperty=nameWithType>|
|**unsigned int** i **unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|
|**__int64** i **podpisany __int64**|<xref:System.Int64?displayProperty=nameWithType>|
|**__int64 bez znaku**|<xref:System.UInt64?displayProperty=nameWithType>|
|**float**|<xref:System.Single?displayProperty=nameWithType>|
|**podwójne** i **typu long double**|<xref:System.Double?displayProperty=nameWithType>|

Aby uzyskać więcej informacji na temat opcji kompilatora jako domyślna na podpisane lub niepodpisane **char**, zobacz [/J (domyślny typ char jest niepodpisany)](../build/reference/j-default-char-type-is-unsigned.md).

## <a name="version_issues"></a> Problemy z wersją w przypadku typów wartości zagnieżdżonych w typach natywnych

Należy wziąć pod uwagę składnika zestawu podpisem (silnej nazwy), używany do tworzenia zestawu klienta. Składnik zawiera typ wartości, który jest używany w kliencie jako typ członka natywnych Unii, klasę lub tablica. Przyszłych wersjach składnika zmiany rozmiaru oraz układu typu wartości, klient musi ponownie kompilowana.

Utwórz keyfile z [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).

### <a name="example"></a>Przykład

Poniższy przykład jest składnikiem.

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>Przykład

Klient jest w tym przykładzie:

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>Dane wyjściowe

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>Komentarze

Jednak jeśli dodasz innego członka do `struct S` w nested_value_types.cpp, (na przykład `double d;`) i skompiluj ponownie składnik bez konieczności ponownego kompilowania klienta, wynik jest nieobsługiwany wyjątek (typu <xref:System.IO.FileLoadException?displayProperty=fullName>).

## <a name="test_equality"></a> Jak: Testowanie dla równości

W poniższym przykładzie test pod kątem równości, który używa zarządzanych rozszerzeń dla C++ opiera się na co uchwytów dotyczą.

### <a name="example"></a>Przykład

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

IL dla tego programu pokazuje, że wartość zwracana jest implementowany przy użyciu wywołania op_equality —.

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="diagnose_fix"></a> Jak: Diagnozowanie i rozwiązywanie problemów ze zgodnością zestawu

W tym temacie opisano, co może się zdarzyć, gdy wersja zestawu z odwołaniem w czasie kompilacji nie odpowiada wersji zestawu, do których odwołuje się w czasie wykonywania oraz sposób uniknąć tego problemu.

Podczas kompilowania zestawu innych zestawów może się odwoływać za pomocą `#using` składni. Podczas kompilacji te zestawy są dostępne przez kompilator. Informacje z tych zestawów są używane do podejmowania decyzji dotyczących optymalizacji.

Jednak jeśli przywoływanego zestawu jest zmienione, a ponownie skompilowana, a nie zostanie ponownie skompilowana odwołujący się zestaw, który jest zależne od tego, zestawy mogą nie być zgodne. Decyzje o optymalizacji, które były prawidłowe w najpierw może nie być prawidłowe w odniesieniu do nowej wersji zestawu. Z powodu niezgodności mogą wystąpić różne błędy czasu wykonywania. Nie ma określonego wyjątku wytworzonego w takich przypadkach. Sposób, w jaki błąd jest zgłaszany w czasie wykonywania zależy od charakteru zmiany kodu, który spowodował problem.

Te błędy nie powinien być problemu w kodzie produkcyjnym końcowego, tak długo, jak cała aplikacja zostanie ponownie skompilowany dla pełnej wersji produktu. Zestawy, które są wydawane publicznie powinien być oznaczony przez numer wersji oficjalnej, który zapewni uniknąć tych problemów. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](/dotnet/framework/app-domains/assembly-versioning).

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnozowanie i rozwiązywanie błędów niezgodności

1. Jeśli występują wyjątki środowiska uruchomieniowego lub inne błędy występujące w kodzie, który odwołuje się do innego zestawu i mają żadne inne określone przyczyny, może być Obsługa nieaktualna zestawu.

1. Najpierw należy wyizolować i odtworzenia wyjątek lub innych warunków błędów. Problem, który występuje z powodu nieaktualnych wyjątku należy do odtworzenia.

1. Sprawdź sygnaturę czasową wszelkich zestawów, do których odwołuje się do aplikacji.

1. W przypadku nowszych niż sygnatura czasowa ostatniej kompilacji aplikacji znacznikami czasu dowolne zestawy, do którego istnieje odwołanie, aplikacja jest nieaktualna. Jeśli ten problem wystąpi, ponownie skompilować aplikację przy użyciu najbardziej aktualnych zestawu i wprowadzać żadnych zmian kodu wymaganych.

1. Uruchom ponownie aplikację, wykonaj kroki odtworzenia problemu, a następnie sprawdź, czy nie występuje wyjątek.

### <a name="example"></a>Przykład

Następujący program ilustruje problem przez zmniejszenie dostępność metody i podjęcie próby na dostęp do tej metody w innym zestawie, bez konieczności ponownego kompilowania. Spróbuj skompilować `changeaccess.cpp` pierwszy. Jest to przywoływanego zestawu, co spowoduje zmianę. Następnie skompilować `referencing.cpp`. Kompilacja zakończy się pomyślnie. Teraz Zmniejsz dostępność metody wywoływanej metody. Skompiluj ponownie `changeaccess.cpp` z flagą `/DCHANGE_ACCESS`. To sprawia, że metoda chronionych, a nie prywatne, dzięki czemu będzie można ją wywołać prawnie. Bez konieczności ponownego kompilowania `referencing.exe`, uruchom ponownie aplikację. Wyjątek <xref:System.MethodAccessException> spowoduje.

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Współdziałanie z innymi językami .NET (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[Typy zarządzane (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using — dyrektywa](../preprocessor/hash-using-directive-cpp.md)
