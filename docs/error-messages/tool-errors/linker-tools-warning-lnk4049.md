---
title: Ostrzeżenie LNK4049 narzędzi konsolidatora
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: b527d15310dba70c1bae21e601db17db2900e219
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674256"
---
# <a name="linker-tools-warning-lnk4049"></a>Ostrzeżenie LNK4049 narzędzi konsolidatora

> symbol "*symbol*"zdefiniowane w"*filename.obj*" jest importowany

[__declspec(DllImport)](../../cpp/dllexport-dllimport.md) określono *symbol* nawet, jeśli symbol jest zdefiniowany w pliku obiektu *filename.obj* w ten sam obraz. Usuń `__declspec(dllimport)` modyfikator, aby rozwiązać tego ostrzeżenia.

## <a name="remarks"></a>Uwagi

To ostrzeżenie jest generowana przez konsolidator, gdy zdefiniować symbol w jeden obiekt pliku i odwoływać się do niego przy użyciu `__declspec(dllimport)` modyfikator deklaracji w innym.

Ostrzeżenie LNK4049 jest nieco bardziej ogólnych [LNK4217 ostrzeżenie narzędzi konsolidatora](linker-tools-warning-lnk4217.md). Konsolidator generuje ostrzeżenie LNK4049, gdy nie można określić, plik, który funkcji lub obiektu odwołanie do symbolu zaimportowane.

Typowe przypadki, gdzie LNK4049 jest generowany zamiast LNK4217 są następujące:

- Korzystając z [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) opcji.

- Korzystając z [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opcji.

Aby rozwiązać LNK4049, wypróbuj jedną z następujących procedur:

- Usuń `__declspec(dllimport)` modyfikator z deklaracją do przodu, który wyzwolił LNK4049 symbolu. Można wyszukiwać symbole w obrębie obrazów binarnych, za pomocą **DUMPBIN** narzędzia. **DUMPBIN /SYMBOLS** przełącznik wyświetla tabelą symboli COFF obrazu. Aby uzyskać więcej informacji na temat **DUMPBIN** narzędzia, zobacz [odwołanie DUMPBIN](../../build/reference/dumpbin-reference.md).

- Aby tymczasowo wyłączyć przyrostowe konsolidowanie i optymalizacji całego programu. Gdy ponownie skompilowana, aplikacja generuje ostrzeżenie LNK4217, która zawiera nazwę funkcji, która odwołuje się do zaimportowanych symboli. Usuń `__declspec(dllimport)` modyfikator deklaracji z zaimportowanych symboli i ponownie Włącz konsolidację przyrostową lub optymalizacja całego programu, zgodnie z potrzebami.

Mimo że końcowy wygenerowany kod działa poprawnie, kod wygenerowany w wywołaniu funkcji importowanych jest mniej wydajne niż bezpośrednie wywoływanie funkcji. To ostrzeżenie nie jest wyświetlany podczas kompilowania przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcji.

Aby uzyskać więcej informacji na temat Importowanie i eksportowanie danych deklaracji, zobacz [dllexport i dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Przykład

Łączenie dwóch następujących modułów wygeneruje LNK4049. Pierwszy moduł generuje obiekt zawierający pojedynczy wyeksportowanej funkcji.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

Drugi moduł generuje plik obiektu zawierającego deklaracją do przodu do funkcji wyeksportowany w module pierwszy wraz z wywołania tę funkcję wewnątrz `main` funkcji. Ten moduł przy użyciu pierwszego modułu konsolidacji wygeneruje LNK4049. Usuń `__declspec(dllimport)` modyfikator z deklaracji, aby rozwiązać ostrzeżenia.

```cpp
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

## <a name="see-also"></a>Zobacz także

[Linker Tools Warning LNK4217](linker-tools-warning-lnk4217.md) \
[Linker Tools Warning LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)