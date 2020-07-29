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
ms.openlocfilehash: 77dc6dc14efe2a7ccf46c41477ed4fd6d1956856
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224035"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)

Możesz eksportować dane, funkcje, klasy lub funkcje składowe klasy z biblioteki DLL za pomocą **`__declspec(dllexport)`** słowa kluczowego. **`__declspec(dllexport)`** dodaje dyrektywę Export do pliku obiektu, aby nie trzeba było używać pliku. def.

Ta wygoda jest najbardziej oczywista podczas próby wyeksportowania dekoracyjnych nazw funkcji języka C++. Ze względu na to, że nie istnieje standardowa Specyfikacja dekoracji nazwy, nazwa wyeksportowanej funkcji może ulec zmianie między wersjami kompilatora. Jeśli używasz **`__declspec(dllexport)`** , ponowne kompilowanie biblioteki DLL i zależne pliki exe są niezbędne tylko w przypadku zmiany konwencji nazewnictwa.

Wiele dyrektyw eksportu, takich jak liczby porządkowe, NONAME i PRIVATE, można wprowadzać tylko w pliku. def i nie ma możliwości określenia tych atrybutów bez pliku. def. Jednak użycie **`__declspec(dllexport)`** programu oprócz użycia pliku. def nie powoduje błędów kompilacji.

Aby wyeksportować funkcje, **`__declspec(dllexport)`** słowo kluczowe musi pojawić się po lewej stronie słowa kluczowego konwencji wywoływania, jeśli słowo kluczowe jest określone. Na przykład:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Aby wyeksportować wszystkie publiczne elementy członkowskie danych i funkcje członkowskie w klasie, słowo kluczowe musi pojawić się po lewej stronie nazwy klasy w następujący sposób:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`nie można zastosować do funkcji z `__clrcall` konwencją wywoływania.

Podczas kompilowania biblioteki DLL zwykle tworzony jest plik nagłówkowy zawierający prototypy i/lub klasy, które są eksportowane i dodawane **`__declspec(dllexport)`** do deklaracji w pliku nagłówkowym. Aby kod był bardziej czytelny, zdefiniuj makro dla **`__declspec(dllexport)`** i użyj makra z każdym eksportowanym symbolem:

```
#define DllExport   __declspec( dllexport )
```

**`__declspec(dllexport)`** przechowuje nazwy funkcji w tabeli eksportu biblioteki DLL. Jeśli chcesz zoptymalizować rozmiar tabeli, zobacz [Eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików. def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportowanie funkcji C do użycia w plikach wykonywalnych języka C lub C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Wybieranie metody eksportowania do użycia](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Słowo kluczowe __declspec](../cpp/declspec.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Importy wzajemne](mutual-imports.md)

## <a name="see-also"></a>Zobacz także

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
