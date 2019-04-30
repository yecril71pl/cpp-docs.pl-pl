---
title: Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
ms.openlocfilehash: ee9d77920f04f7eba5112c66a906b02b7fc4a658
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384429"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)

Program .NET Framework zawiera jawne wywołanie platformy (lub jako PInvoke) funkcji `Dllimport` atrybutu, aby umożliwić aplikacji zarządzanych do wywołania funkcji niezarządzanych spakowane wewnątrz biblioteki dll. Jawnej funkcji PInvoke jest wymagana dla sytuacji, w którym niezarządzanych interfejsów API są spakowane w postaci bibliotek DLL i kod źródłowy jest niedostępny. Na przykład, wywołanie funkcji Win32 wymaga PInvoke. W przeciwnym razie użyj niejawnego P {Invoke; zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) Aby uzyskać więcej informacji.

Mechanizm PInvoke działa, korzystając z <xref:System.Runtime.InteropServices.DllImportAttribute>. Ten atrybut, który przyjmuje nazwę biblioteki DLL jako swój pierwszy argument, jest umieszczany przed deklaracji funkcji, dla każdego punktu wejścia biblioteki DLL, który będzie używany. Podpis funkcji musi być zgodna z nazwą funkcji eksportowanych przez DLL (ale niektóre konwersji typów może zostać wykonana niejawnie przez zdefiniowanie `DllImport` deklaracji pod względem typów zarządzanych.)

Wynik jest zarządzany punkt wejścia dla każdej natywnej funkcji biblioteki DLL, która zawiera kod konieczne przejście (lub thunk) i konwersje prostych danych. Następnie wywołać zarządzanej funkcji do biblioteki DLL za pomocą tych punktów wejścia. Kod dodaje do modułu, w wyniku funkcji PInvoke jest całkowicie zarządzana.

## <a name="in-this-section"></a>W tej sekcji

- [Wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md)

- [Instrukcje: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów za pomocą funkcji PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [Instrukcje: przeprowadzanie marshalingu struktur za pomocą funkcji PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [Instrukcje: przeprowadzanie marshalingu tablic za pomocą funkcji PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [Instrukcje: przeprowadzanie marshalingu wskaźników funkcji za pomocą funkcji PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [Instrukcje: przeprowadzanie marshalingu wskaźników osadzonych za pomocą funkcji PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>Zobacz także

[Wywoływanie funkcji natywnych z kodu zarządzanego](../dotnet/calling-native-functions-from-managed-code.md)
