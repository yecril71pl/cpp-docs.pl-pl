---
title: 'Porady: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ddd919fb621c971425e9763cf781e5ff0b1c731
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195671"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Porady: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke
Funkcje, które są implementowane w niezarządzanych bibliotek DLL może być wywołana z kodu zarządzanego za pomocą funkcji wywołania platformy (P/Invoke). Jeśli kod źródłowy dla biblioteki DLL nie jest dostępna, P/Invoke jest jedyną opcją dla współpracy. Jednak w przeciwieństwie do innych języków .NET, Visual C++ stanowi alternatywę dla metody P/Invoke. Aby uzyskać więcej informacji, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa Win32 [GetSystemMetrics](https://msdn.microsoft.com/library/windows/desktop/ms724385) funkcję, aby pobrać aktualna rozdzielczość ekranu w pikselach.  
  
 Dla funkcji, które używają tylko typy wewnętrzne jako argumenty i zwracać wartości nie dodatkowej pracy jest wymagana. Inne typy danych, takich jak wskaźniki funkcji, tablic i struktur, wymagają dodatkowe atrybuty, aby upewnić się, organizowanie odpowiednie dane.  
  
 Chociaż nie jest wymagane, jest dobrą praktyką, aby powiększyć P/Invoke deklaracje statyczne elementy członkowskie klasy wartości, dzięki czemu nie istnieją w globalnej przestrzeni nazw, jak pokazano w tym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)