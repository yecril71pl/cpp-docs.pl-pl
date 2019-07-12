---
title: Omówienie marshalingu w języku C++
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 937fbdf4b3ed09344e69a8f1eb731565c36794ae
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861170"
---
# <a name="overview-of-marshaling-in-ccli"></a>Omówienie Marshalingu w C++sposób niezamierzony

W trybie mieszanym czasami musisz zarządzać dane między typami macierzystym i zarządzanym. *Biblioteka dotycząca organizowania* pomaga kierować i przekonwertować danych w prosty sposób.  Biblioteka dotycząca organizowania zawiera zestaw funkcji i `marshal_context` klasy służące do przeprowadzania marshaling dla popularnych typów. Biblioteka jest zdefiniowany w tych nagłówków w **obejmują msclr** katalog dla posiadanej wersji programu Visual Studio:

|nagłówek|Opis|
|---------------|-----------------|
|marshal.h|`marshal_context` klasy i funkcje organizowania bezpłatne kontekstu|
|marshal_atl.h| Funkcje dla marshaling typów ATL|
|marshal_cppstd.h|Funkcje na przekazywanie standardowych typów języka C++|
|marshal_windows.h|Marshaling typów Windows funkcji|

Domyślna ścieżka dla **msclr** folder jest podobny do poniższego w zależności od używanej wersji masz i numer kompilacji:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Można użyć Biblioteka dotycząca organizowania z lub bez [marshal_context Class](../dotnet/marshal-context-class.md). Niektóre konwersje wymaga kontekstu. Inne konwersje można zaimplementować przy użyciu [marshal_as](../dotnet/marshal-as.md) funkcji. W tabeli poniżej wymieniono konwersje bieżący obsługiwany, czy kontekst jest wymagany i jakie pliku marshal powinien obejmować:

|Z typu|Na typ|Metoda Marshal|Dołącz plik|
|---------------|-------------|--------------------|------------------|
|System::String ^|Const char \*|marshal_context|marshal.h|
|Const char \*|System::String ^|marshal_as|marshal.h|
|Char \*|System::String ^|marshal_as|marshal.h|
|System::String ^|Const wchar_t\*|marshal_context|marshal.h|
|Const wchar_t \*|System::String ^|marshal_as|marshal.h|
|wchar_t \*|System::String ^|marshal_as|marshal.h|
|System::IntPtr|UCHWYT|marshal_as|marshal_windows.h|
|UCHWYT|System::IntPtr|marshal_as|marshal_windows.h|
|System::String ^|BSTR|marshal_context|marshal_windows.h|
|BSTR|System::String ^|marshal_as|marshal.h|
|System::String ^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System::String ^|marshal_as|marshal_windows.h|
|System::String ^|std::string|marshal_as|marshal_cppstd.h|
|std::string|System::String ^|marshal_as|marshal_cppstd.h|
|System::String ^|STD::wstring|marshal_as|marshal_cppstd.h|
|STD::wstring|System::String ^|marshal_as|marshal_cppstd.h|
|System::String ^|CStringT\<char>|marshal_as|marshal_atl.h|
|CStringT\<char>|System::String ^|marshal_as|marshal_atl.h|
|System::String ^|CStringT < wchar_t >|marshal_as|marshal_atl.h|
|CStringT < wchar_t >|System::String ^|marshal_as|marshal_atl.h|
|System::String ^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System::String ^|marshal_as|marshal_atl.h|

Marshaling wymaga kontekstu, tylko wtedy, gdy kierować dane zarządzanego do natywnych typów i typu macierzystego, który jest konwertowane na nie ma destruktora do automatycznego czyszczenia. Marshaling kontekstu niszczy przydzielone macierzystego typu danych w jego destruktor. W związku z tym konwersje, które wymagają kontekstu, będzie obowiązywał tylko do momentu kontekst zostanie usunięty. Aby zapisać wszystkie zorganizowanej wartości, należy skopiować wartości do własnych zmiennych.

> [!NOTE]
>  Po osadzeniu `NULL`s w ciągu, wynikiem marshaling ciąg nie jest gwarantowana. Osadzonego `NULL`s może spowodować, że ciągu obcięte lub mogą one zostać zachowane.

W tym przykładzie pokazano jak dołączyć katalogu msclr w deklaracji nagłówka include:

`#include "msclr\marshal_cppstd.h"`

Biblioteka organizatora jest rozszerzalny, tak, aby można było dodać organizowania typów. Aby uzyskać więcej informacji na temat rozszerzania Biblioteka dotycząca organizowania, zobacz [jak: Rozszerzanie biblioteki Marshalingu](../dotnet/how-to-extend-the-marshaling-library.md).

## <a name="see-also"></a>Zobacz także

[Biblioteka obsługi języka C++](../dotnet/cpp-support-library.md)<br/>
[Instrukcje: rozszerzanie biblioteki marshalingu](../dotnet/how-to-extend-the-marshaling-library.md)
