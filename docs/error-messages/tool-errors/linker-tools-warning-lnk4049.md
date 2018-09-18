---
title: Ostrzeżenie LNK4049 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ad4e4adb492789639c71a25a2db774a80cd77c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021762"
---
# <a name="linker-tools-warning-lnk4049"></a>Ostrzeżenie LNK4049 narzędzi konsolidatora

lokalnie zdefiniowany symbol "symbol" zaimportowany

Symbol został wyeksportowany z i zaimportowany do programu.

To ostrzeżenie jest generowana przez konsolidator przy deklarowaniu symbol za pomocą `__declspec(dllexport)` klasę magazynu atrybutów w jeden obiekt pliku i odwoływać się do niego przy użyciu `__declspec(dllimport)` atrybutu w innym.

Ostrzeżenie LNK4049 jest nieco bardziej ogólnych [LNK4217 ostrzeżenie narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). Konsolidator generuje ostrzeżenie LNK4049, gdy nie można określić, z funkcji odwołanie do symbolu zaimportowane.

Typowe przypadki, gdzie LNK4049 jest generowany zamiast LNK4217 są następujące:

- Wykonywanie przyrostowe konsolidowanie za pomocą [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) opcji.

- Przeprowadzania optymalizacji całego programu za pomocą [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opcji.

Aby rozwiązać LNK4049, wypróbuj jedną z następujących czynności:

- Usuń `__declspec(dllimport)` Nazwa deklaracji z deklaracją do przodu symbolu, która wywołała LNK4049. Można wyszukiwać symbole w obrębie obrazów binarnych, za pomocą **DUMPBIN** narzędzia. **DUMPBIN/symbole** przełącznik wyświetla tabelą symboli COFF obrazu. Aby uzyskać więcej informacji na temat **DUMPBIN** narzędzia, zobacz [odwołanie DUMPBIN](../../build/reference/dumpbin-reference.md).

- Aby tymczasowo wyłączyć przyrostowe konsolidowanie i optymalizacji całego programu. Wygeneruje ostrzeżenie LNK4217, która będzie obejmować nazwę funkcji, z którego wystąpiło odwołanie do symbolu importowanych ponownego kompilowania aplikacji. Usuń `__declspec(dllimport)` deklaracji z zaimportowanych symboli i Włącz konsolidację przyrostową lub optymalizacja całego programu, zgodnie z potrzebami.

Mimo że końcowy wygenerowany kod będzie działać prawidłowo, kod wygenerowany w wywołaniu funkcji importowanych jest mniej wydajne niż bezpośrednie wywoływanie funkcji. To ostrzeżenie nie będą widoczne, gdy kompilujesz przy użyciu opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

Aby uzyskać więcej informacji na temat Importowanie i eksportowanie danych deklaracji, zobacz [dllexport i dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Przykład

Łączenie dwóch następujących modułów wygeneruje LNK4049. Pierwszy moduł generuje obiekt zawierający pojedynczy wyeksportowanej funkcji.

```
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

## <a name="example"></a>Przykład

Drugi moduł generuje plik obiektu zawierającego deklaracją do przodu do funkcji wyeksportowany w module pierwszy wraz z wywołania tę funkcję wewnątrz `main` funkcji. Ten moduł przy użyciu pierwszego modułu konsolidacji wygeneruje LNK4049. Usuwanie `__declspec(dllimport)` deklaracji rozwiąże to ostrzeżenie.

```
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>Zobacz też

[Ostrzeżenie narzędzi konsolidatora LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)