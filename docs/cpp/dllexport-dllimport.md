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
ms.openlocfilehash: f03c945375cbe8c399e604e12f070b5a63d316f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221656"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Specyficzne dla firmy Microsoft**

**`dllexport`** **`dllimport`** Atrybuty klasy magazynu i są rozszerzeniami specyficznymi dla firmy Microsoft do języków C i C++. Można ich użyć do eksportowania i importowania funkcji, danych i obiektów do lub z biblioteki DLL.

## <a name="syntax"></a>Składnia

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Uwagi

Te atrybuty jawnie definiują interfejs biblioteki DLL dla klienta, który może być plikiem wykonywalnym lub inną biblioteką DLL. Deklarowanie funkcji jako **`dllexport`** eliminuje konieczność użycia pliku definicji modułu (. def), co najmniej w odniesieniu do specyfikacji eksportowanych funkcji. Ten **`dllexport`** atrybut zastępuje słowo kluczowe **__export** .

Jeśli klasa jest oznaczona jako declspec (dllexport), wszystkie specjalizacje szablonów klas w hierarchii klas są niejawnie oznaczone jako declspec (dllexport). Oznacza to, że szablony klas są jawnie tworzone, a elementy członkowskie klasy muszą być zdefiniowane.

**`dllexport`** funkcja udostępnia funkcję z nazwą dekoracyjną. W przypadku funkcji języka C++ obejmuje to nazwę dekorowanie. W przypadku funkcji lub funkcji języka C, które są zadeklarowane jako `extern "C"` , obejmuje to specyficzną dla platformy dekorację opartą na konwencji wywoływania. Aby uzyskać informacje dotyczące dekoracji nazw w kodzie C/C++, zobacz [dekoracyjne nazwy](../build/reference/decorated-names.md). Do wyeksportowanych funkcji C lub funkcji języka C++ `extern "C"` przy użyciu konwencji wywoływania nie są stosowane dekoracje nazw **`__cdecl`** .

Aby wyeksportować niedekoracyjną nazwę, można połączyć się przy użyciu pliku definicji modułu (. def), który definiuje nazwę niedekoracyjną w sekcji EKSPORTy. Aby uzyskać więcej informacji, zobacz [eksporty](../build/reference/exports.md). Innym sposobem eksportowania niedekoracyjnej nazwy jest użycie `#pragma comment(linker, "/export:alias=decorated_name")` dyrektywy w kodzie źródłowym.

Gdy deklarujesz **`dllexport`** lub **`dllimport`** , musisz użyć [rozszerzonej składni atrybutów](../cpp/declspec.md) i **`__declspec`** słowa kluczowego.

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

- [Definiowanie wbudowanych funkcji języka C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [Ogólne zasady i ograniczenia](../cpp/general-rules-and-limitations.md)

- [Używanie dllimport i dllexport w klasach C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
