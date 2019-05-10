---
title: Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
- __declspec
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 167060d0270004b8648d32af206865bfe66c3b4b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220792"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)

Możesz wyeksportować dane, funkcje, klasy lub funkcje składowych klasy z biblioteki DLL za pomocą **__declspec(dllexport)** — słowo kluczowe. **__declspec(dllexport)** dodaje dyrektywy Eksport do pliku obiektu, dzięki czemu nie trzeba używać pliku .def.

To udogodnienie jest najbardziej widoczne podczas próby wyeksportowania dekorowane nazwy funkcji języka C++. Ponieważ nie ma żadnych standardowych specyfikacji dla dekoracji nazwy, nazwa eksportowanych funkcji może ulec zmianie między wersjami kompilatora. Jeśli używasz **__declspec(dllexport)**, ponowna kompilacja biblioteki DLL i zależnych plików .exe jest konieczna tylko konta do dla dowolnych zmian konwencji nazewnictwa.

Wiele dyrektyw dotyczących eksportowania takich jak liczby porządkowe, bez nazwy i prywatnych, jest możliwe tylko w pliku .def i nie ma sposobu określania tych atrybutów bez pliku .def. Jednak przy użyciu **__declspec(dllexport)** oprócz używania .def pliku nie powoduje błędy kompilacji.

Aby eksportować funkcje **__declspec(dllexport)** — słowo kluczowe musi znajdować się po lewej stronie słowa kluczowego konwencji wywołania, jeśli jest określone słowo kluczowe. Na przykład:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Aby wyeksportować wszystkie publiczne elementy członkowskie danych i funkcji składowych w klasie, słowo kluczowe musi wyświetlić się po lewej stronie nazwy klasy w następujący sposób:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` Nie można zastosować do funkcji z `__clrcall` konwencji wywoływania.

Kompilując DLL, zwykle tworzysz plik nagłówka, który zawiera prototypy funkcji i/lub klasy, które eksportujesz lub dodajesz **__declspec(dllexport)** do deklaracji w pliku nagłówkowym. Aby zwiększyć czytelność kodu, zdefiniuj makro dla **__declspec(dllexport)** i użyj makra z każdym symbolem, który eksportujesz:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** przechowuje nazwy funkcji w tabeli eksportu biblioteki DLL. Jeśli chcesz zoptymalizować rozmiar tabeli, zobacz [eksportowanie funkcji z biblioteki DLL według liczby porządkowej zamiast nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików .def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportuj funkcje C do użycia w plikach wykonywalnych języka C lub języka C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Określić, której metody eksportowania użyjesz](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Zainicjuj bibliotekę DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [__Declspec — słowo kluczowe](../cpp/declspec.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Importy wzajemne](mutual-imports.md)

## <a name="see-also"></a>Zobacz także

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
