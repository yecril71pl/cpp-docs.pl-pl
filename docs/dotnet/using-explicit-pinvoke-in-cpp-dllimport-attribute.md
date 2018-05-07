---
title: Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 82215e4815d25dd116cf930be9cc0f40da761bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)
Platforma .NET Framework zapewnia jawnego wywołania platformy (lub funkcji PInvoke) funkcji z `Dllimport` atrybutu aby umożliwić aplikacjom zarządzanym wywołaniem funkcji niezarządzanej umieszczone wewnątrz biblioteki dll. Jawnej funkcji PInvoke jest wymagany w sytuacjach, w którym pakiecie niezarządzane interfejsy API w postaci bibliotek DLL i kod źródłowy jest niedostępny. Na przykład podczas wywoływania funkcji Win32 wymaga funkcji PInvoke. W przeciwnym razie użyj P niejawne {Invoke; zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) Aby uzyskać więcej informacji.  
  
 PInvoke działa przy użyciu <xref:System.Runtime.InteropServices.DllImportAttribute>. Ten atrybut, który przyjmuje nazwę biblioteki DLL jako pierwszego argumentu, jest umieszczana przed deklaracji funkcji dla każdego punktu wejścia biblioteki DLL, który będzie używany. Podpis funkcji musi odpowiadać nazwie funkcji wyeksportowane przez bibliotekę DLL (, ale niektóre konwersji typów może zostać wykonana niejawnie przez zdefiniowanie `DllImport` deklaracje pod względem typy zarządzane.)  
  
 Wynik jest zarządzany punkt wejścia dla każdej natywnej funkcji DLL, która zawiera kod niezbędne przejścia (lub thunk) i konwersje proste danych. Funkcje zarządzanej można wywoływać w bibliotece DLL przez te punkty wejścia. Kod wstawione do modułu w wyniku PInvoke całkowicie jest zarządzana.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [Instrukcje: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów za pomocą funkcji PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu struktur za pomocą funkcji PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu tablic za pomocą funkcji PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu wskaźników funkcji za pomocą funkcji PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu wskaźników osadzonych za pomocą funkcji PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md)