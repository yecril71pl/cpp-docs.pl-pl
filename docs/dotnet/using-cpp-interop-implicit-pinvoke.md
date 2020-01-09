---
title: Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)
ms.date: 11/04/2016
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
ms.openlocfilehash: d26fbefd87b3ba6d6ca7e183be78608777f383b5
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/06/2020
ms.locfileid: "75676930"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)

W przeciwieństwie do innych języków .NET C++ , Wizualizacja ma obsługę współdziałania, która umożliwia kod zarządzany i niezarządzany w tej samej aplikacji, a nawet w tym samym pliku (z [zarządzanymi, niezarządzanymi](../preprocessor/managed-unmanaged.md) pragmami). Dzięki temu deweloperzy C++ wizualni mogą zintegrować funkcje platformy .NET C++ z istniejącymi aplikacjami wizualnymi bez zakłócania pozostałej części aplikacji.

Można również wywołać funkcje niezarządzane z zarządzanego jednostka kompilacji przy użyciu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Niejawny PInvoke jest przydatny, gdy nie trzeba określać, jak będą organizowane parametry funkcji lub inne szczegóły, które można określić podczas jawnego wywoływania elementu DllImportAttribute.

Wizualizacja C++ zapewnia dwa sposoby współdziałania z funkcjami zarządzanymi i niezarządzanymi:

- [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

Jawna wartość PInvoke jest obsługiwana przez .NET Framework i jest dostępna w większości języków .NET. Ale jako że jego nazwa oznacza, C++ międzyoperacyjność jest specyficzna dla wizualizacji C++.

## <a name="c-interop"></a>międzyoperacyjność C++

C++Międzyoperacyjność zapewnia lepszą bezpieczeństwo typów i jest zazwyczaj mniej żmudnym do wdrożenia. Jednak C++ międzyoperacyjność nie jest opcją, jeśli niezarządzany kod źródłowy jest niedostępny lub dla projektów międzyplatformowych.

## <a name="c-com-interop"></a>współdziałanie języka C++ z modelem COM

Funkcje współdziałania obsługiwane przez C++ wizualizację zapewniają konkretną korzyść w porównaniu z innymi językami .NET, gdy chodzi o współdziałanie ze składnikami modelu com. Zamiast ograniczać się do ograniczeń .NET Framework [Tlbimp. exe (Importer biblioteki typów)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), takich jak ograniczona obsługa typów danych i obowiązkowe narażenie każdego członka każdego z interfejsów COM, C++ międzyoperacyjność umożliwia dostęp do składników com w programie i nie wymaga oddzielnych zestawów międzyoperacyjnych. W przeciwieństwie do C#Visual Basic i C++ , Wizualizacja może używać obiektów com bezpośrednio przy użyciu standardowych mechanizmów com (takich jak funkcja **CoCreateInstance** i polecenie **QueryInterface**). Jest to możliwe z powodu C++ funkcji międzyoperacyjnych, które powodują, że kompilator automatycznie wstawi kod przejścia do przenoszenia z zarządzanych do funkcji niezarządzanych i ponownie z powrotem.

Za C++ pomocą międzyoperacyjności można używać składników com, ponieważ są one zwykle używane lub mogą być opakowane wewnątrz C++ klas. Te klasy otoki są nazywane niestandardowymi otokami w środowisku uruchomieniowym lub CRCWs i mają dwie zalety użycia modelu COM bezpośrednio w kodzie aplikacji:

- Klasa będąca wynikiem może być używana z języków innych niż C++Visual.

- Szczegóły interfejsu COM można ukryć w kodzie zarządzanego klienta. Typy danych platformy .NET mogą być używane zamiast typów natywnych, a szczegółowe informacje o kierowaniu danych mogą być wykonywane w sposób przezroczysty wewnątrz CRCW.

Bez względu na to, czy COM jest używany bezpośrednio, czy za pomocą CRCW, typy argumentów inne niż proste, typy danych kopiowalnych muszą być organizowane.

## <a name="blittable-types"></a>Typy danych kopiowalnych

W przypadku niezarządzanych interfejsów API, które używają prostych typów wewnętrznych (zobacz [typy danych kopiowalnych i inne niż danych kopiowalnych](/dotnet/framework/interop/blittable-and-non-blittable-types)), nie jest wymagane żadne specjalne kodowanie, ponieważ te typy danych mają tę samą reprezentację w pamięci, ale bardziej złożone typy danych wymagają jawnego organizowania danych. Aby zapoznać się z przykładem, zobacz [jak: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

## <a name="example"></a>Przykład

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>W tej sekcji

- [Instrukcje: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu struktur za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu tablic za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu wskaźników osadzonych za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [Instrukcje: dostęp do znaków w obiekcie System::String](../dotnet/how-to-access-characters-in-a-system-string.md)

- [Instrukcje: konwertowanie ciągu char * na tablicę System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [Instrukcje: konwertowanie system:: String na wchar_t * lub char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Instrukcje: konwertowanie obiektu System::String na ciąg standardowy](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Instrukcje: konwertowanie ciągu standardowego na obiekt System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Instrukcje: uzyskiwanie wskaźnika do tablicy typu Byte](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Instrukcje: ładowanie zasobów niezarządzanych do tablicy typu Byte](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Instrukcje: modyfikowanie klasy odwołań w funkcji natywnej](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Instrukcje: ustalanie, czy obraz jest obrazem natywnym, czy CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Instrukcje: dodawanie natywnej biblioteki DLL do globalnej pamięci podręcznej zestawów](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Instrukcje: utrzymywanie odwołania do typu wartości w typie natywnym](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Instrukcje: utrzymywanie odwołania do obiektu w pamięci niezarządzanej](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Instrukcje: Wykrywanie kompilacji/CLR](../dotnet/how-to-detect-clr-compilation.md)

- [Instrukcje: konwertowanie między identyfikatorami System::Guid i _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Instrukcje: określanie parametru wyjściowego](../dotnet/how-to-specify-an-out-parameter.md)

- [Instrukcje: korzystanie z typu natywnego w kompilacji/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Instrukcje: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md)

- [Instrukcje: opakowywanie klasy natywnej do użycia w języku C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Aby uzyskać informacje na temat korzystania z delegatów w scenariuszu międzyoperacyjnym, zobacz [Delegat (C++ Component Extensions)](../extensions/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Zobacz także

- [Wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md)
