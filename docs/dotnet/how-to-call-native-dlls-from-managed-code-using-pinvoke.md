---
title: 'Instrukcje: Wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: b36496690c4d83837a6dff1752f3f0db514869eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501236"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Instrukcje: Wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke

Funkcje zaimplementowane w niezarządzanych bibliotekach DLL mogą być wywoływane z kodu zarządzanego za pomocą funkcji wywołania platformy (P/Invoke). Jeśli kod źródłowy biblioteki DLL nie jest dostępny, Metoda P/Invoke jest jedyną opcją dla współdziałania. Jednak, w przeciwieństwie do innych języków .NET C++ , Wizualizacja stanowi alternatywę dla P/Invoke. Aby uzyskać więcej informacji, [Zobacz C++ using Interop (niejawny PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu używa funkcji Win32 [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) , aby pobrać bieżącą rozdzielczość ekranu w pikselach.

W przypadku funkcji używających tylko typów wewnętrznych jako argumentów i wartości zwracanych nie jest wymagana żadna dodatkowa liczba zadań. Inne typy danych, takie jak wskaźniki funkcji, tablice i struktury, wymagają dodatkowych atrybutów, aby zapewnić prawidłowe kierowanie danych.

Chociaż nie jest to wymagane, dobrym sposobem jest wykonywanie deklaracji P/Invoke statycznych elementów członkowskich klasy wartości, tak aby nie istniały w globalnej przestrzeni nazw, jak pokazano w tym przykładzie.

```
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>Zobacz także

[Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
