---
title: 'Porady: kierowanie wskaźników osadzonych za pomocą funkcji PInvoke | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a07c9742c393abe2a6213378ee8963839ab66c90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134900"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Porady: przeprowadzanie marshalingu wskaźników osadzonych za pomocą funkcji PInvoke
Funkcje, które zostały wdrożone w niezarządzanych bibliotek DLL może zostać wywołana z kodu zarządzanego za pomocą funkcji wywołania platformy (P/Invoke). Jeśli kod źródłowy dla biblioteki DLL nie jest dostępna, P/Invoke jest jedyną opcją dla współpracy. Jednak w przeciwieństwie do innych języków .NET, Visual C++ stanowi alternatywę dla P/Invoke. Aby uzyskać więcej informacji, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) i [porady: kierowanie osadzonych wskaźników za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).  
  
## <a name="example"></a>Przykład  
 Przekazywanie struktur do kodu macierzystego wymaga utworzenia zarządzanych struktura, która odpowiada pod względem danych układu natywnego struktury. Jednak struktur, które zawierają wskaźniki wymagają specjalnej obsługi. Dla każdego wskaźnika osadzony w strukturze macierzystego, zarządzanej wersji struktury powinien zawierać wystąpienie <xref:System.IntPtr> typu. Ponadto pamięci dla tych wystąpień musi być jawnie przydzielona, zainicjować i zwolniony przy użyciu <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>, i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> metody.  
  
 Poniższy kod składa się z modułu zarządzanych i niezarządzanych. Moduł niezarządzanym jest bibliotekę DLL, która definiuje funkcję, która akceptuje strukturę o nazwie ListString, który zawiera wskaźnik i funkcji o nazwie TakesListStruct. Moduł zarządzany jest aplikacją wiersza polecenia, który importuje funkcja TakesListStruct i definiuje strukturę o nazwie MListStruct, który jest odpowiednikiem natywnego ListStruct z tą różnicą, że o podwójnej precyzji * odpowiada z <xref:System.IntPtr> wystąpienia. Przed wywołaniem metody TakesListStruct, funkcja main przydziela i inicjuje pamięci, która odwołuje się do tego pola.  
  
```cpp  
// TraditionalDll6.cpp  
// compile with: /EHsc /LD  
#include <stdio.h>  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
#pragma pack(push, 8)  
struct ListStruct {  
   int count;  
   double* item;  
};  
#pragma pack(pop)  
  
extern "C" {  
   TRADITIONALDLL_API void TakesListStruct(ListStruct);  
}  
  
void TakesListStruct(ListStruct list) {  
   printf_s("[unmanaged] count = %d\n", list.count);  
   for (int i=0; i<list.count; i++)  
      printf_s("array[%d] = %f\n", i, list.item[i]);  
}  
```  
  
```cpp  
// EmbeddedPointerMarshalling.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, Pack=8)]  
value struct MListStruct {  
   int count;  
   IntPtr item;  
};  
  
value struct TraditionalDLL {  
    [DllImport("TraditionalDLL6.dll")]  
   static public void TakesListStruct(MListStruct);  
};  
  
int main() {  
   array<double>^ parray = gcnew array<double>(10);  
   Console::WriteLine("[managed] count = {0}", parray->Length);  
  
   Random^ r = gcnew Random();  
   for (int i=0; i<parray->Length; i++) {  
      parray[i] = r->NextDouble() * 100.0;  
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);  
   }  
  
   int size = Marshal::SizeOf(double::typeid);  
   MListStruct list;  
   list.count = parray->Length;  
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);  
  
   for (int i=0; i<parray->Length; i++) {  
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);  
      Marshal::StructureToPtr(parray[i], t, false);  
   }  
  
   TraditionalDLL::TakesListStruct( list );  
   Marshal::FreeCoTaskMem(list.item);  
}  
```  
  
 Należy pamiętać, że żadna jego część biblioteki DLL jest narażony na kod zarządzany przy użyciu tradycyjnych # dyrektywy include. W rzeczywistości biblioteki DLL jest dostępny tylko w czasie wykonywania, problemy z funkcjami zaimportowane z <xref:System.Runtime.InteropServices.DllImportAttribute> nie zostanie wykryty w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)