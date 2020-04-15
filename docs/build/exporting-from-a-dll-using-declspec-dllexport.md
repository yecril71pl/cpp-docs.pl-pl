---
title: Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328591"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)

Można eksportować dane, funkcje, klasy lub funkcje członkowskie klasy z biblioteki DLL przy użyciu słowa kluczowego **__declspec(dllexport).** **__declspec(dllexport)** dodaje dyrektywę eksportu do pliku obiektu, dzięki czemu nie trzeba używać pliku def.

Ta wygoda jest najbardziej widoczne podczas próby eksportowania dekoracyjne nazwy funkcji C++. Ponieważ nie istnieje standardowa specyfikacja dekoracji nazw, nazwa eksportowanej funkcji może ulec zmianie między wersjami kompilatora. Jeśli używasz **__declspec(dllexport),** ponowne skompilowanie biblioteki DLL i zależnych plików exe jest konieczne tylko do uwzględnienia wszelkich zmian konwencji nazewnictwa.

Wiele dyrektyw eksportowych, takich jak liczby porządkowe, NONAME i PRIVATE, można zrobić tylko w pliku def i nie ma możliwości określenia tych atrybutów bez pliku def. Jednak użycie **__declspec(dllexport)** oprócz użycia pliku def nie powoduje błędów kompilacji.

Aby wyeksportować funkcje, słowo kluczowe **__declspec(dllexport)** musi być wyświetlane po lewej stronie słowa kluczowego konwencji wywołania, jeśli określono słowo kluczowe. Przykład:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Aby wyeksportować wszystkie elementy członkowskie danych publicznych i funkcje członkowskie w klasie, słowo kluczowe musi być wyświetlane po lewej stronie nazwy klasy w następujący sposób:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`nie można zastosować do funkcji `__clrcall` z konwencją wywołującą.

Podczas tworzenia biblioteki DLL zazwyczaj należy utworzyć plik nagłówka zawierający prototypy funkcji i/lub klasy, które są eksportowane i dodać **__declspec(dllexport)** do deklaracji w pliku nagłówka. Aby kod był bardziej czytelny, zdefiniuj makro dla **__declspec(dllexport)** i użyj makra z każdym eksportowanym symbolem:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** przechowuje nazwy funkcji w tabeli eksportu biblioteki DLL. Aby zoptymalizować rozmiar tabeli, zobacz [Eksportowanie funkcji z biblioteki DLL według nazwy porządkowej, a nie według nazwy.](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL przy użyciu plików def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji języka C++ do użytku w plikach wykonywalnych w języku C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportowanie funkcji C do użytku w plikach wykonywalnych języka C lub C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Określanie, która metoda eksportowania ma być używana](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>O czym chcesz wiedzieć więcej?

- [Słowo kluczowe __declspec](../cpp/declspec.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Wzajemny przywóz](mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
