---
title: dllexport i dllimport | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dllimport_cpp
- dllexport_cpp
dev_langs:
- C++
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75a2e31e62d9899c2e287c5fca7ad5dfdcc67311
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078169"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Microsoft Specific**

**Dllexport** i **dllimport** atrybuty klasy magazynu są rozszerzeniami specyficzne dla firmy Microsoft do języków C i C++. Można ich użyć do eksportowania i importowania funkcji, danych i obiektów do i z biblioteki DLL.

## <a name="syntax"></a>Składnia

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Uwagi

Atrybuty te jawnie definiują interfejs DLL dla jego klienta, który może być plikiem wykonawczym lub innym DLL. Deklarowanie funkcji jako **dllexport** eliminuje potrzebę stosowania pliku definicji modułu (.def), co najmniej w odniesieniu do specyfikacji eksportowanych funkcji. **Dllexport** atrybutu zastępuje **__export** — słowo kluczowe.

Jeśli klasa jest oznaczona declspec(dllexport), wszystkie specjalizacje szablonów klas w hierarchii klas są niejawnie oznaczone jako declspec(dllexport). Oznacza to, że szablony klas są jawnie tworzone i elementy członkowskie klas muszą być zdefiniowane.

**dllexport** funkcja udostępnia funkcję z nazwy dekoracyjnej. W przypadku funkcji C++ obejmuje to dekorowanie nazw. Dla funkcji języka C lub funkcji, które są zadeklarowane jako `extern "C"`, obejmuje to dekorację specyficzną dla platformy, który jest oparty na konwencji wywoływania. Aby uzyskać informacji na temat dekorowania nazw w kodzie języka C/C++, zobacz [nazwy dekorowane](../build/reference/decorated-names.md). Nie dekorowania nazw jest stosowany do eksportowanych funkcji języka C lub C++ `extern "C"` funkcji przy użyciu `__cdecl` konwencji wywoływania.

Aby wyeksportować nieozdobioną nazwę, możesz połączyć przy użyciu pliku definicji modułu (.def), który definiuje nieozdobioną nazwę zawartej w sekcji. Aby uzyskać więcej informacji, zobacz [EKSPORTY](../build/reference/exports.md). Innym sposobem, aby wyeksportować nieozdobioną nazwę jest użycie `#pragma comment(linker, "/export:alias=decorated_name")` dyrektywę w kodzie źródłowym.

Kiedy Deklarujesz **dllexport** lub **dllimport**, należy użyć [rozszerzonej składni atrybutu](../cpp/declspec.md) i **__declspec** — słowo kluczowe.

## <a name="example"></a>Przykład

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

Ewentualnie Aby zwiększyć czytelność kodu, można użyć definicje makr:

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)