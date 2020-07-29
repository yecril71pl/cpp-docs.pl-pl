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
ms.openlocfilehash: c542151bda780e5306db35049d988e6514fffd62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225608"
---
# <a name="managed-types-ccli"></a>Typy zarządzane (C++/CLI)

Visual C++ umożliwia dostęp do funkcji platformy .NET za pomocą typów zarządzanych, które zapewniają obsługę funkcji środowiska uruchomieniowego języka wspólnego i są objęte zaletami i ograniczeniami środowiska uruchomieniowego.

## <a name="managed-types-and-the-main-function"></a><a name="main_functions"></a>Typy zarządzane i funkcja Main

Podczas pisania aplikacji przy użyciu **`/clr`** , argumenty funkcji **Main ()** nie mogą być typu zarządzanego.

Przykładem właściwej sygnatury jest:

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="net-framework-equivalents-to-c-native-types"></a><a name="dotnet"></a>.NET Framework odpowiedników typów natywnych języka C++

W poniższej tabeli przedstawiono słowa kluczowe dla wbudowanych typów Visual C++, które są aliasami wstępnie zdefiniowanych typów w przestrzeni nazw **system** .

|Typ Visual C++|Typ programu .NET Framework|
|-----------------------|-------------------------|
|**`void`**|<xref:System.Void?displayProperty=nameWithType>|
|**`bool`**|<xref:System.Boolean?displayProperty=nameWithType>|
|**`signed char`** |<xref:System.SByte?displayProperty=nameWithType>|
|**`unsigned char`**|<xref:System.Byte?displayProperty=nameWithType>|
|**`wchar_t`**|<xref:System.Char?displayProperty=nameWithType>|
|**`short`** lub**`signed short`**|<xref:System.Int16?displayProperty=nameWithType>|
|**`unsigned short`**|<xref:System.UInt16?displayProperty=nameWithType>|
|**`int`**, **`signed int`** , **`long`** i**`signed long`**|<xref:System.Int32?displayProperty=nameWithType>|
|**`unsigned int`** lub**`unsigned long`**|<xref:System.UInt32?displayProperty=nameWithType>|
|**`__int64`** lub**`signed __int64`**|<xref:System.Int64?displayProperty=nameWithType>|
|**`unsigned __int64`**|<xref:System.UInt64?displayProperty=nameWithType>|
|**`float`**|<xref:System.Single?displayProperty=nameWithType>|
|**`double`** lub**`long double`**|<xref:System.Double?displayProperty=nameWithType>|

Aby uzyskać więcej informacji na temat opcji kompilatora, która jest domyślną wartością **`signed char`** lub **`unsigned char`** , zobacz [ `/J` (domyślny **`char`** Typ to **`unsigned`** )](../build/reference/j-default-char-type-is-unsigned.md).

## <a name="version-issues-for-value-types-nested-in-native-types"></a><a name="version_issues"></a>Problemy z wersją w przypadku typów wartości zagnieżdżonych w typach natywnych

Rozważmy podpisany składnik zestawu (silna nazwa) używany do kompilowania zestawu klienta. Składnik zawiera typ wartości, który jest używany w kliencie jako typ elementu członkowskiego Unii natywnej, klasy lub tablicy. Jeśli przyszła wersja składnika zmienia rozmiar lub układ typu wartości, należy ponownie skompilować klienta.

Utwórz element KeyFile z [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) ( `sn -k mykey.snk` ).

### <a name="example"></a>Przykład

Poniższy przykład to składnik.

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

Ten przykład jest klientem:

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

Jeśli jednak dodasz inny element członkowski do `struct S` programu w nested_value_types. cpp, (na przykład `double d;` ) i ponownie skompilujesz składnik bez ponownego kompilowania klienta, wynikiem jest nieobsługiwany wyjątek (typu <xref:System.IO.FileLoadException?displayProperty=fullName> ).

## <a name="how-to-test-for-equality"></a><a name="test_equality"></a>Instrukcje: testowanie pod kątem równości

W poniższym przykładzie test dla równości, który używa Managed Extensions for C++ jest oparty na tym, do czego odnoszą się uchwyty.

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

IL dla tego programu pokazuje, że wartość zwracana jest implementowana przy użyciu wywołania do op_Equality.

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="how-to-diagnose-and-fix-assembly-compatibility-problems"></a><a name="diagnose_fix"></a>Instrukcje: diagnozowanie i rozwiązywanie problemów ze zgodnością zestawów

W tym temacie wyjaśniono, co może się zdarzyć, gdy wersja zestawu, do którego odwołuje się w czasie kompilacji, nie jest zgodna z wersją zestawu, do którego odwołuje się w czasie wykonywania, i jak uniknąć problemu.

Gdy zestaw jest kompilowany, inne zestawy mogą być przywoływane ze `#using` składnią. Podczas kompilowania te zestawy są dostępne dla kompilatora. Informacje z tych zestawów są używane w celu podejmowania decyzji dotyczących optymalizacji.

Jeśli jednak przywoływany zestaw zostanie zmieniony i ponownie skompilowany, a nie zostanie ponownie skompilowana odwołującego się zestawu, który jest od niego zależny, zestawy mogą nie być zgodne. Decyzje dotyczące optymalizacji, które były prawidłowe w pierwszej kolejności, mogą nie być poprawne w odniesieniu do nowej wersji zestawu. Przyczyną niezgodności mogą być różne błędy środowiska uruchomieniowego. Nie ma konkretnego wyjątku, który zostanie wygenerowany w takich przypadkach. Sposób zgłoszenia błędu w czasie wykonywania zależy od rodzaju zmiany kodu, która spowodowała problem.

Te błędy nie powinny być problemem w końcowym kodzie produkcyjnym, o ile cała aplikacja zostanie odbudowana dla wydanej wersji produktu. Zestawy, które są udostępniane publicznie, powinny być oznaczone oficjalnym numerem wersji, co zapewni uniknięcie tych problemów. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](/dotnet/framework/app-domains/assembly-versioning).

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnozowanie i rozwiązywanie błędu niezgodności

1. Jeśli wystąpią wyjątki środowiska uruchomieniowego lub inne warunki błędu występujące w kodzie, który odwołuje się do innego zestawu, i nie ma żadnych innych zidentyfikowanych przyczyn, może się okazać, że jest to nieaktualne zestawienie.

1. Najpierw Izoluj i Odtwarzaj wyjątek lub inny warunek błędu. Wystąpił problem spowodowany nieaktualnym wyjątkem.

1. Sprawdź sygnaturę czasową wszelkich zestawów, do których odwołuje się aplikacja.

1. Jeśli sygnatury czasowe dowolnego przywoływanych zestawów są późniejsze niż sygnatura czasowa ostatniej kompilacji aplikacji, aplikacja jest nieaktualna. W takim przypadku należy ponownie skompilować aplikację przy użyciu najnowszego zestawu i wprowadzić wymagane zmiany kodu.

1. Uruchom ponownie aplikację, wykonaj kroki, które odtwarzają problem i sprawdź, czy nie wystąpił wyjątek.

### <a name="example"></a>Przykład

Poniższy program ilustruje problem, zmniejszając dostępność metody i próbując uzyskać dostęp do tej metody w innym zestawie bez ponownego kompilowania. Najpierw spróbuj skompilować `changeaccess.cpp` . Jest to przywoływany zestaw, który zostanie zmieniony. Następnie Skompiluj `referencing.cpp` . Kompilacja powiodła się. Teraz Zmniejsz dostępność wywołanej metody. Kompiluj ponownie `changeaccess.cpp` z flagą `/DCHANGE_ACCESS` . Dzięki temu Metoda jest chroniona, a nie prywatna, więc można ją już wywoływać legalnie. Bez ponownej kompilacji `referencing.exe` ponownie uruchom aplikację. Spowoduje to <xref:System.MethodAccessException> powstanie wyjątku.

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
