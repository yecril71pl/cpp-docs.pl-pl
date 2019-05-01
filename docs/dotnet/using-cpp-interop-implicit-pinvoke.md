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
ms.openlocfilehash: aaa07373b7dd22807290ceefa9197b4013c61fe5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384520"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)

W przeciwieństwie do innych języków .NET, Visual C++ obsługuje współdziałanie umożliwiająca kodem zarządzanym i niezarządzanym istnieć w tej samej aplikacji, a nawet w tym samym pliku (z [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) pragm). Dzięki temu Visual C++ deweloperom na integrowanie funkcji .NET istniejących aplikacji Visual C++ bez naruszania pozostałe części aplikacji.

Można również wywołać funkcji niezarządzanych z zarządzanego compiland — za pomocą [dllexport i dllimport](../cpp/dllexport-dllimport.md).

Niejawna funkcja PInvoke jest przydatne, gdy potrzebujesz określić, jak będą przekazywane parametry funkcji lub dowolne inne szczegóły, które można określić podczas wywoływania jawnie DllImportAttribute.

Visual C++ zapewnia dwa sposoby zarządzanych i niezarządzanych funkcji pod kątem współdziałania:

- [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

Jawnej funkcji PInvoke jest obsługiwana przez program .NET Framework i jest dostępna w większości języków platformy .NET. Ale jak sugeruje jej nazwa, międzyoperacyjności języka C++ jest specyficzny dla języka Visual C++.

## <a name="c-interop"></a>międzyoperacyjność C++

Ponieważ zapewnia lepsze bezpieczeństwo typów, jest zwykle było mniej uciążliwe do wdrożenia, jest bardziej forgiving, jeśli niezarządzanego interfejsu API jest modyfikowany i sprawia, że możliwe ulepszenia wydajności, która nie jest możliwa za pomocą jawnego międzyoperacyjności języka C++ zaleca się za pośrednictwem jawnej funkcji PInvoke Mechanizm PInvoke. Jednak międzyoperacyjności języka C++ nie jest możliwe, jeśli kod źródłowy niezarządzane nie jest dostępna.

## <a name="c-com-interop"></a>współdziałanie języka C++ z modelem COM

Funkcje współpracy, obsługiwane przez Visual C++ oferuje określonego przewagę nad innymi językami .NET, jeśli chodzi o współpracy ze składnikami modelu COM. W przeciwieństwie do ograniczenia dotyczące programu .NET Framework [Tlbimp.exe (Importer biblioteki typów)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), takich jak ograniczoną obsługę typów danych i wymagane ujawnienia każdy członek każdego interfejsu COM, międzyoperacyjności języka C++ umożliwia COM składniki, które były dostępne w będzie i nie jest wymagane oddzielne zestawy międzyoperacyjne. W przeciwieństwie do języka Visual Basic i C#, Visual C++ można użyć obiektów COM bezpośrednio przy użyciu zwykłych mechanizmów COM (takie jak **CoCreateInstance** i **QueryInterface**). Jest to możliwe z powodu cechy międzyoperacyjności języka C++, które powodują automatyczne wstawianie kodu przejścia, aby przenieść z zarządzanych w niezarządzanych funkcji i z powrotem przez kompilator.

Za pomocą międzyoperacyjności języka C++, składników COM może służyć jako są zwykle używane lub może zostać zawinięty wewnątrz klasy C++. Te klasy otoki są nazywane wywoływanych otok środowiska uruchomieniowego niestandardowych lub CRCWs, dlatego ma dwie korzyści za pośrednictwem za pomocą modelu COM bezpośrednio w kodzie aplikacji:

- Klasa wynikowa może służyć w językach innych niż Visual C++.

- Szczegóły interfejsu COM mogą być ukrywane z kodu zarządzanego klienta. Typy danych .NET można użyć zamiast natywnych typów i szczegóły przekazywania danych mogą być wykonywane w sposób niewidoczny dla użytkownika wewnątrz CRCW.

Niezależnie od tego, czy COM jest używany, bezpośrednio lub za pośrednictwem CRCW można zorganizować typy argumentów niż prosty, typy danych kopiowalnych.

## <a name="blittable-types"></a>Typy Kopiowalne

Do niezarządzanych interfejsów API Użyj typów prostych, wewnętrzne (zobacz [Kopiowalne i typy danych Kopiowalnych inne niż](/dotnet/framework/interop/blittable-and-non-blittable-types)), bez kodowania jest wymagana, ponieważ te typy danych mają tę samą reprezentację w pamięci, ale wymagają bardziej złożone typy danych marshaling danych jawnego. Aby uzyskać przykład, zobacz [jak: Wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

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

- [Instrukcje: Konwertowanie obiektu System::String na wchar_t * lub char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

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

- [Instrukcje: Używanie typu natywnego w kompilacji/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Instrukcje: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md)

- [Instrukcje: opakowywanie klasy natywnej do użycia w języku C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Aby uzyskać informacji dotyczących używania delegatów w scenariuszu międzyoperacyjnych, zobacz [delegate (C++ Component Extensions)](../extensions/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Zobacz także

- [Wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md)
