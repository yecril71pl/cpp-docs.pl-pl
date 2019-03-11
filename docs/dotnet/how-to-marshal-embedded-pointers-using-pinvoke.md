---
title: 'Instrukcje: Przeprowadzanie marshalingu wskaźników osadzonych za pomocą funkcji PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
ms.openlocfilehash: 943a1a2784a37353157cd38da7ebdc9827006fe5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738755"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Instrukcje: Przeprowadzanie marshalingu wskaźników osadzonych za pomocą funkcji PInvoke

Funkcje, które są implementowane w niezarządzanych bibliotek DLL może być wywołana z kodu zarządzanego za pomocą funkcji wywołania platformy (P/Invoke). Jeśli kod źródłowy dla biblioteki DLL nie jest dostępna, P/Invoke jest jedyną opcją dla współpracy. Jednak w przeciwieństwie do innych języków .NET, Visual C++ stanowi alternatywę dla metody P/Invoke. Aby uzyskać więcej informacji, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) i [jak: Przeprowadzanie marshalingu wskaźników osadzonych za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

## <a name="example"></a>Przykład

Przekazywanie struktury do kodu macierzystego wymaga utworzenia zarządzanej strukturę, która jest równoważna pod względem układ danych natywnych struktury. Jednakże struktur, które zawierają wskaźniki wymagają specjalnej obsługi. Dla każdego wskaźnika osadzone w strukturze natywnego, zarządzanego wersję struktury powinien zawierać wystąpienia <xref:System.IntPtr> typu. Ponadto pamięci dla tych wystąpień musi jawnie przydzielone, zainicjować i wydania przy użyciu <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>, i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> metody.

Poniższy kod składa się z modułu zarządzanego i niezarządzanego. Moduł niezarządzane to biblioteki DLL, która definiuje funkcję, która akceptuje strukturę o nazwie ListString, który zawiera wskaźnik i funkcję o nazwie TakesListStruct. Moduł zarządzany jest aplikacją wiersza polecenia, który importuje funkcja TakesListStruct i definiuje strukturę o nazwie MListStruct, który jest odpowiednikiem ListStruct macierzysty, z tą różnicą, że podwójne * jest reprezentowane przez <xref:System.IntPtr> wystąpienia. Przed wywołaniem TakesListStruct, główna funkcja przydziela i inicjuje pamięć, która odwołuje się do tego pola.

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

Należy pamiętać, że części biblioteki DLL jest uwidaczniany związane z kodem zarządzanym przy użyciu tradycyjnych # dyrektywy include. W rzeczywistości biblioteki DLL jest dostępny tylko w czasie wykonywania, więc problemy z funkcjami zaimportowane wraz z <xref:System.Runtime.InteropServices.DllImportAttribute> nie zostanie wykryty w czasie kompilacji.

## <a name="see-also"></a>Zobacz także

[Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
