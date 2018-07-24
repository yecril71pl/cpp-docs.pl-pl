---
title: Omówienie Marshalingu w języku C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 747d9a67f7796b5a62115acf55343370aea77bdf
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207868"
---
# <a name="overview-of-marshaling-in-c"></a>Omówienie marshalingu w języku C++
W trybie mieszanym czasami musisz zarządzać dane między typami macierzystym i zarządzanym. Program Visual Studio 2008 wprowadzono *Biblioteka dotycząca organizowania* ułatwiające kierować i przekonwertować danych w prosty sposób.  Biblioteka dotycząca organizowania zawiera zestaw funkcji i `marshal_context` klasy służące do przeprowadzania marshaling dla popularnych typów. Biblioteka jest zdefiniowany w tych nagłówków w **obejmują msclr** katalog dla posiadanej wersji programu Visual Studio:

|nagłówek|Opis|  
|---------------|-----------------|
|Marshal.h|`marshal_context` klasy i funkcje organizowania bezpłatne kontekstu|
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
|System::String ^|Const char \*|marshal_context|Marshal.h|  
|Const char \*|System::String ^|marshal_as|Marshal.h|  
|Char \*|System::String ^|marshal_as|Marshal.h|  
|System::String ^|Const wchar_t\*|marshal_context|Marshal.h|  
|Const wchar_t \*|System::String ^|marshal_as|Marshal.h|  
|wchar_t \*|System::String ^|marshal_as|Marshal.h|  
|System::IntPtr|UCHWYT|marshal_as|marshal_windows.h|  
|UCHWYT|System::IntPtr|marshal_as|marshal_windows.h|  
|System::String ^|BSTR|marshal_context|marshal_windows.h|  
|BSTR|System::String ^|marshal_as|Marshal.h|  
|System::String ^|bstr_t|marshal_as|marshal_windows.h|  
|bstr_t|System::String ^|marshal_as|marshal_windows.h|  
|System::String ^|STD::String|marshal_as|marshal_cppstd.h|  
|STD::String|System::String ^|marshal_as|marshal_cppstd.h|  
|System::String ^|STD::wstring|marshal_as|marshal_cppstd.h|  
|STD::wstring|System::String ^|marshal_as|marshal_cppstd.h|  
|System::String ^|CStringT\<char >|marshal_as|marshal_atl.h|  
|CStringT\<char >|System::String ^|marshal_as|marshal_atl.h|  
|System::String ^|CStringT < wchar_t >|marshal_as|marshal_atl.h|  
|CStringT < wchar_t >|System::String ^|marshal_as|marshal_atl.h|  
|System::String ^|CComBSTR|marshal_as|marshal_atl.h|  
|CComBSTR|System::String ^|marshal_as|marshal_atl.h|  
  
 Marshaling wymaga kontekstu, tylko wtedy, gdy kierować dane zarządzanego do natywnych typów i typu macierzystego, który jest konwertowane na nie ma destruktora do automatycznego czyszczenia. Marshaling kontekstu niszczy przydzielone macierzystego typu danych w jego destruktor. W związku z tym konwersje, które wymagają kontekstu, będzie obowiązywał tylko do momentu kontekst zostanie usunięty. Aby zapisać wszystkie zorganizowanej wartości, należy skopiować wartości do własnych zmiennych.  
  
> [!NOTE]
>  Po osadzeniu `NULL`s w ciągu, wynikiem marshaling ciąg nie jest gwarantowana. Osadzonego `NULL`s może spowodować, że ciągu obcięte lub mogą one zostać zachowane.  
  
W tym przykładzie pokazano jak dołączyć katalogu msclr w deklaracji nagłówka include:  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 Biblioteka organizatora jest rozszerzalny, tak, aby można było dodać organizowania typów. Aby uzyskać więcej informacji na temat rozszerzania Biblioteka dotycząca organizowania, zobacz [porady: rozszerzanie biblioteki Marshalingu](../dotnet/how-to-extend-the-marshaling-library.md).  
  
 We wcześniejszych wersjach, można kierować dane za pomocą [wywołania platformy](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Aby uzyskać więcej informacji na temat `PInvoke`, zobacz [podczas wywoływania funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka obsługi języka C++](../dotnet/cpp-support-library.md)   
 [Instrukcje: rozszerzanie biblioteki marshalingu](../dotnet/how-to-extend-the-marshaling-library.md)
