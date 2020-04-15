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
ms.openlocfilehash: 0c7bf18fa823c6301a79c3f989efa73c9e8f628a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372010"
---
# <a name="overview-of-marshaling-in-ccli"></a>Omówienie marshalingu w języku C++/CLI

W trybie mieszanym czasami należy zorganizować dane między typami macierzystymi i zarządzanymi. *Biblioteka organizowania* ułatwia organizowanie i konwertowanie danych w prosty sposób.  Biblioteka organizowania składa się z `marshal_context` zestawu funkcji i klasy, które wykonują kierowanie dla typowych typów. Biblioteka jest zdefiniowana w tych nagłówkach w katalogu **include/msclr** dla wersji programu Visual Studio:

|Nagłówek|Opis|
|---------------|-----------------|
|marszałek.h|`marshal_context`funkcje organizowania bez klas i kontekstu|
|marshal_atl.h| Funkcje organizowania typów ATL|
|marshal_cppstd.h|Funkcje organizowania standardowych typów języka C++|
|marshal_windows.h|Funkcje organizowania typów systemu Windows|

Domyślna ścieżka dla folderu **msclr** jest coś takiego w zależności od wersji, którą masz i numer kompilacji:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Można użyć biblioteki organizowania z [klasą marshal_context](../dotnet/marshal-context-class.md)lub bez . Niektóre konwersje wymagają kontekstu. Inne konwersje można zaimplementować za pomocą funkcji [marshal_as.](../dotnet/marshal-as.md) W poniższej tabeli wymieniono bieżące konwersje obsługiwane, czy wymagają one kontekstu i jaki plik marshal należy dołączyć:

|Od typu|Aby wpisać|Metoda marszałka|Dołącz plik|
|---------------|-------------|--------------------|------------------|
|System::Ciąg^|const char (char)\*|marshal_context|marszałek.h|
|const char (char)\*|System::Ciąg^|marshal_as|marszałek.h|
|Char\*|System::Ciąg^|marshal_as|marszałek.h|
|System::Ciąg^|wchar_t\*|marshal_context|marszałek.h|
|wchar_t\*|System::Ciąg^|marshal_as|marszałek.h|
|Wchar_t\*|System::Ciąg^|marshal_as|marszałek.h|
|System::IntPtr|Obsługi|marshal_as|marshal_windows.h|
|Obsługi|System::IntPtr|marshal_as|marshal_windows.h|
|System::Ciąg^|Bstr|marshal_context|marshal_windows.h|
|Bstr|System::Ciąg^|marshal_as|marszałek.h|
|System::Ciąg^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System::Ciąg^|marshal_as|marshal_windows.h|
|System::Ciąg^|Std::string|marshal_as|marshal_cppstd.h|
|Std::string|System::Ciąg^|marshal_as|marshal_cppstd.h|
|System::Ciąg^|Std::wstring|marshal_as|marshal_cppstd.h|
|Std::wstring|System::Ciąg^|marshal_as|marshal_cppstd.h|
|System::Ciąg^|> char\<CStringT|marshal_as|marshal_atl.h|
|> char\<CStringT|System::Ciąg^|marshal_as|marshal_atl.h|
|System::Ciąg^|><wchar_t CStringT|marshal_as|marshal_atl.h|
|><wchar_t CStringT|System::Ciąg^|marshal_as|marshal_atl.h|
|System::Ciąg^|Ccombstr|marshal_as|marshal_atl.h|
|Ccombstr|System::Ciąg^|marshal_as|marshal_atl.h|

Kierowanie wymaga kontekstu tylko wtedy, gdy marshal z zarządzanych do natywnych typów danych i typu macierzystego, który konwertujesz nie ma destruktora do automatycznego oczyszczania. Kontekst organizowania niszczy przydzielony typ danych natywnych w jego destruktora. W związku z tym konwersje, które wymagają kontekstu będą prawidłowe tylko do momentu usunięcia kontekstu. Aby zapisać wszystkie wartości organizowane, należy skopiować wartości do własnych zmiennych.

> [!NOTE]
> Jeśli masz osadzone `NULL`s w ciągu, wynik kierowanie ciąg nie jest gwarantowana. Osadzone `NULL`s może spowodować ciąg do obciętej lub mogą być zachowane.

W tym przykładzie pokazano, jak uwzględnić katalog msclr w deklaracji nagłówka include:

`#include "msclr\marshal_cppstd.h"`

Biblioteka organizowania jest rozszerzalny, dzięki czemu można dodać własne typy marshaling. Aby uzyskać więcej informacji na temat rozszerzania biblioteki organizowania, zobacz [Jak: Rozszerzanie biblioteki marshaling .](../dotnet/how-to-extend-the-marshaling-library.md)

## <a name="see-also"></a>Zobacz też

[Biblioteka obsługi języka C++](../dotnet/cpp-support-library.md)<br/>
[Instrukcje: rozszerzanie biblioteki marshalingu](../dotnet/how-to-extend-the-marshaling-library.md)
