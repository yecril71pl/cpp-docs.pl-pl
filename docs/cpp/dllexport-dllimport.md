---
title: dllexport, dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: 0a8d90770552b8b9ab9169378289108d91811216
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189458"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Specyficzne dla firmy Microsoft**

Atrybuty klasy magazynu **dllexport** i **dllimport** są rozszerzeniami specyficznymi dla firmy Microsoft do języków C C++ i. Można ich użyć do eksportowania i importowania funkcji, danych i obiektów do lub z biblioteki DLL.

## <a name="syntax"></a>Składnia

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Uwagi

Te atrybuty jawnie definiują interfejs biblioteki DLL dla klienta, który może być plikiem wykonywalnym lub inną biblioteką DLL. Deklarowanie funkcji jako **dllexport** eliminuje konieczność użycia pliku definicji modułu (. def), co najmniej w odniesieniu do specyfikacji funkcji eksportowanych. Atrybut **dllexport** zastępuje słowo kluczowe **__export** .

Jeśli klasa jest oznaczona jako declspec (dllexport), wszystkie specjalizacje szablonów klas w hierarchii klas są niejawnie oznaczone jako declspec (dllexport). Oznacza to, że szablony klas są jawnie tworzone, a elementy członkowskie klasy muszą być zdefiniowane.

**dllexport** funkcji uwidacznia funkcję z jej dekoracyjną nazwą. W C++ przypadku funkcji jest to nazwa dekorowanie. W przypadku funkcji lub funkcji języka C, które są zadeklarowane jako `extern "C"`, obejmuje to specyficzną dla platformy dekorację opartą na konwencji wywoływania. Aby uzyskać informacje na temat dekoracji nazw wC++ języku C/Code, zobacz [nazwy dekoracyjne](../build/reference/decorated-names.md). Do wyeksportowanych funkcji C lub C++ funkcji `extern "C"` przy użyciu konwencji wywoływania `__cdecl` nie zastosowano dekoracji nazwy.

Aby wyeksportować niedekoracyjną nazwę, można połączyć się przy użyciu pliku definicji modułu (. def), który definiuje nazwę niedekoracyjną w sekcji EKSPORTy. Aby uzyskać więcej informacji, zobacz [eksporty](../build/reference/exports.md). Innym sposobem eksportowania niedekoracyjnej nazwy jest użycie dyrektywy `#pragma comment(linker, "/export:alias=decorated_name")` w kodzie źródłowym.

Podczas deklarowania **dllexport** lub **dllimport**należy użyć [składni atrybutów rozszerzonych](../cpp/declspec.md) i słowa kluczowego **__declspec** .

## <a name="example"></a>Przykład

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

Alternatywnie, aby kod był bardziej czytelny, można użyć definicji makr:

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

Aby uzyskać więcej informacji, zobacz:

- [Definicje i deklaracje](../cpp/definitions-and-declarations-cpp.md)

- [Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [Ograniczenia i reguły ogólne](../cpp/general-rules-and-limitations.md)

- [Korzystanie z dllimport i dllexport w klasach C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
