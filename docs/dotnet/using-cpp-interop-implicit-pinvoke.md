---
title: Za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a91c9833358744730b9ad9c63f5a14729d9d0968
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-c-interop-implicit-pinvoke"></a>Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)
W przeciwieństwie do innych języków .NET, Visual C++ obsługuje współdziałania umożliwiający zarządzane i niezarządzane kod, mogą znajdować się w tej samej aplikacji, a nawet w tym samym pliku (z [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) pragm). Dzięki temu Visual C++ deweloperom zintegrowanie funkcji .NET do istniejących aplikacji Visual C++, bez zakłócania pozostałej części aplikacji.  
  
 Możesz także wywołać niezarządzanej funkcji z compiland zarządzanych za pomocą [dllexport i dllimport](../cpp/dllexport-dllimport.md).  
  
 PInvoke — niejawna metoda jest przydatne, gdy trzeba określić sposób można zorganizować parametry funkcji lub szczegóły, które można określić podczas jawnego wywołania elementu DllImportAttribute.  
  
 Visual C++ udostępnia dwa sposoby zarządzane i niezarządzane funkcji na potrzeby współdziałania:  
  
-   [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 Jawnej funkcji PInvoke jest obsługiwane przez program .NET Framework i jest dostępna w większości języków .NET. Jednak jak jego nazwa wskazuje, międzyoperacyjności języka C++ jest specyficzne dla Visual C++.  
  
## <a name="c-interop"></a>międzyoperacyjność C++  
 Międzyoperacyjność C++ jest zalecane w jawnej funkcji PInvoke, ponieważ zapewnia lepsze bezpieczeństwo typów, jest zazwyczaj mniej złożone wdrożenia, jest bardziej forgiving, jeśli niezarządzanego API zostanie zmodyfikowana, a sprawia, że możliwe ulepszenia wydajności, które nie są możliwe za pomocą jawnego PInvoke. Jednak międzyoperacyjności języka C++ nie jest możliwe, jeśli kod niezarządzany źródłowy jest niedostępny.  
  
## <a name="c-com-interop"></a>współdziałanie języka C++ z modelem COM  
 Współdziałanie funkcje obsługiwane przez Visual C++ oferują danego zaletą za pośrednictwem innych języków .NET, jeśli chodzi o współdziałanie z COM — składniki. W przeciwieństwie do ograniczeń programu .NET Framework [Tlbimp.exe (Importer biblioteki typów)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), takich jak ograniczoną obsługę typy danych i obowiązkowe narażenie każdy element członkowski każdego interfejsu COM, międzyoperacyjności języka C++ pozwala COM składniki do jest dostępny pod adresem będzie i nie wymaga oddzielne zestawy międzyoperacyjne. Aby uzyskać więcej informacji, zobacz [za pomocą modelu COM z .NET](http://msdn.microsoft.com/en-us/03976661-6278-4227-a6c1-3b3315502c15).  
  
## <a name="blittable-types"></a>Typy Kopiowalne  
 Dla niezarządzanego interfejsów API, które typy proste, wewnętrzne (zobacz [Kopiowalne i typy Kopiowalne inne niż](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3)), nie kodowania są wymagane, ponieważ te typy danych mają taką samą reprezentację w pamięci, ale wymagają bardziej złożone typy danych przekazywanie danych jawnego. Na przykład zobacz [porady: wywołań natywnych bibliotek DLL z zarządzanego kodu za pomocą funkcji PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).  
  
## <a name="example"></a>Przykład  
  
```  
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
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu struktur za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu tablic za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu wskaźników osadzonych za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [Instrukcje: dostęp do znaków w obiekcie System::String](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [Instrukcje: konwertowanie ciągu char * na tablicę System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [Porady: konwertowanie obiektu System::String na wchar_t * lub char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [Instrukcje: konwertowanie obiektu System::String na ciąg standardowy](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [Instrukcje: konwertowanie ciągu standardowego na obiekt System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [Instrukcje: uzyskiwanie wskaźnika do tablicy typu Byte](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [Instrukcje: ładowanie zasobów niezarządzanych do tablicy typu Byte](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [Instrukcje: modyfikowanie klasy odwołań w funkcji natywnej](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [Instrukcje: ustalanie, czy obraz jest obrazem natywnym, czy CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [Instrukcje: dodawanie natywnej biblioteki DLL do globalnej pamięci podręcznej zestawów](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [Instrukcje: utrzymywanie odwołania do typu wartości w typie natywnym](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [Instrukcje: utrzymywanie odwołania do obiektu w pamięci niezarządzanej](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [Porady: wykrywanie kompilacji/CLR](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [Instrukcje: konwertowanie między identyfikatorami System::Guid i _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [Instrukcje: określanie parametru wyjściowego](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [Porady: używanie typu natywnego w kompilacji/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [Instrukcje: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [Instrukcje: opakowywanie klasy natywnej do użycia w języku C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 Uzyskać przy użyciu delegatów w scenariuszu międzyoperacyjnego, zobacz [delegata (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md)