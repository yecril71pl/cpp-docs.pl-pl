---
title: "Omówienie Marshalingu w języku C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9d910c7d6346d23f094e9359f0e5fe3536ee09dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-marshaling-in-c"></a>Omówienie marshalingu w języku C++
W trybie mieszanym możesz czasami należy kierować danych między typami natywnych i zarządzanych. [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)]wprowadzono biblioteki marshalingu w celu organizowania i przekonwertować danych w prosty sposób.  
  
 Możesz użyć biblioteki marshalingu z lub bez [marshal_context — klasa](../dotnet/marshal-context-class.md). Niektóre konwersje wymagają kontekst. Inne konwersje można implementować przy użyciu [marshal_as —](../dotnet/marshal-as.md) funkcji. W poniższej tabeli przedstawiono bieżące konwersje obsługiwane, czy kontekst jest wymagany i jakiego pliku kierowanie musi zawierać:  
  
|Z typu|Wprowadzenie|Kierowanie — metoda|Plik dołączania|  
|---------------|-------------|--------------------|------------------|  
|System::String ^|Const char *|marshal_context —|Marshal.h|  
|Const char *|System::String ^|marshal_as|Marshal.h|  
|char *|System::String ^|marshal_as|Marshal.h|  
|System::String ^|wchar_t const *|marshal_context —|Marshal.h|  
|Const wchar_t *|System::String ^|marshal_as|Marshal.h|  
|wchar_t *|System::String ^|marshal_as|Marshal.h|  
|System::IntPtr|DOJŚCIE|marshal_as|marshal_windows.h|  
|DOJŚCIE|System::IntPtr|marshal_as|marshal_windows.h|  
|System::String ^|BSTR|marshal_context —|marshal_windows.h|  
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
  
 Organizowanie wymaga kontekstu, tylko w przypadku organizowania danych zarządzanego do natywnych typów typu macierzystego, który ma zostać zmieniony na nie ma destruktora do automatycznego czyszczenia. Kontekst kierowania niszczy przydzielone macierzystego typu danych w jego destruktora. W związku z tym konwersje, które wymagają kontekst będzie obowiązywać, aż kontekst zostanie usunięty. Aby zapisać wartości organizowane, należy skopiować wartości do własnych zmiennych.  
  
> [!NOTE]
>  Po osadzeniu `NULL`s w ciągu, wynik organizowanie ciąg nie jest gwarantowana. Osadzonego `NULL`s może powodować ciągu obcięte lub mogą zostać zachowane.  
  
 Nagłówki biblioteki kierowania znajdują się w katalogu include w podkatalogu msclr. W tym przykładzie pokazano, jak dołączyć podanego katalogu msclr w deklaracji Dołącz nagłówek:  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 Biblioteki marshalingu jest otwarty, aby mogli dodawać własne kierowania typy. Aby uzyskać więcej informacji na temat rozszerzanie biblioteki marshalingu, zobacz [porady: rozszerzanie biblioteki Marshalingu](../dotnet/how-to-extend-the-marshaling-library.md).  
  
 W starszych wersjach, można kierować danych przy użyciu [wywołanie platformy](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Aby uzyskać więcej informacji na temat `PInvoke`, zobacz [wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka obsługi języka C++](../dotnet/cpp-support-library.md)   
 [Instrukcje: rozszerzanie biblioteki marshalingu](../dotnet/how-to-extend-the-marshaling-library.md)