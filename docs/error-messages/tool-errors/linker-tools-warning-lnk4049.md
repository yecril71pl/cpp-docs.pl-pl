---
title: Ostrzeżenie LNK4049 narzędzi konsolidatora
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: a8e4416eafd47f584de4ab1c83aa7303cab0440a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194138"
---
# <a name="linker-tools-warning-lnk4049"></a>Ostrzeżenie LNK4049 narzędzi konsolidatora

> Symbol "*symbol*" zdefiniowany w elemencie "*filename. obj*" został zaimportowany

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) została określona dla *symbolu* , chociaż symbol jest zdefiniowany w pliku obiektu *filename. obj* w tym samym obrazie. Usuń modyfikator `__declspec(dllimport)`, aby usunąć to ostrzeżenie.

## <a name="remarks"></a>Uwagi

To ostrzeżenie jest generowane przez konsolidator podczas definiowania symbolu w jednym pliku obiektu i odwoływania się do niego przy użyciu modyfikatora deklaracji `__declspec(dllimport)` w innym.

Ostrzeżenie LNK4049 narzędzi KONSOLIDATORA to bardziej ogólna wersja [narzędzi konsolidatora LNK4217 narzędzi konsolidatora](linker-tools-warning-lnk4217.md). Konsolidator generuje ostrzeżenie LNK4049 narzędzi KONSOLIDATORA, gdy nie może ustalić, który plik funkcji lub obiektu odwołuje się do zaimportowanego symbolu.

Typowe przypadki, w których Wygenerowano LNK4049 narzędzi KONSOLIDATORA zamiast LNK4217 narzędzi KONSOLIDATORA są następujące:

- W przypadku korzystania z opcji [/Incremental](../../build/reference/incremental-link-incrementally.md) .

- W przypadku korzystania z opcji [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) .

Aby rozwiązać LNK4049 narzędzi KONSOLIDATORA, wypróbuj jedną z następujących procedur:

- Usuń modyfikator `__declspec(dllimport)` z deklaracji Forward symbolu, który wyzwolił LNK4049 narzędzi KONSOLIDATORA. Symbole w obrazie binarnym można wyszukiwać za pomocą narzędzia **polecenia DUMPBIN** . Przełącznik **polecenia DUMPBIN/Symbols** Wyświetla tabelę symboli COFF obrazu. Aby uzyskać więcej informacji na temat narzędzia **polecenia DUMPBIN** , zobacz [polecenia DUMPBIN Reference](../../build/reference/dumpbin-reference.md).

- Tymczasowo wyłącz konsolidację przyrostową i optymalizację całego programu. Po ponownym skompilowaniu aplikacja generuje ostrzeżenie LNK4217 narzędzi KONSOLIDATORA, która zawiera nazwę funkcji, która odwołuje się do zaimportowanego symbolu. Usuń modyfikator deklaracji `__declspec(dllimport)` z zaimportowanego symbolu, a następnie ponownie włącz konsolidację przyrostową lub optymalizację całego programu zgodnie z potrzebami.

Mimo że ostatni wygenerowany kod działa prawidłowo, kod wygenerowany do wywołania zaimportowanej funkcji jest mniej wydajny niż bezpośrednie wywoływanie funkcji. To ostrzeżenie nie pojawia się podczas kompilowania przy użyciu opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Aby uzyskać więcej informacji na temat importowania i eksportowania deklaracji danych, zobacz [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Przykład

Łączenie następujących dwóch modułów spowoduje wygenerowanie LNK4049 narzędzi KONSOLIDATORA. Pierwszy moduł generuje plik obiektu zawierający pojedynczą wyeksportowaną funkcję.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

Drugi moduł generuje plik obiektu zawierający deklarację do przodu do funkcji wyeksportowanej w pierwszym module wraz z wywołaniem tej funkcji wewnątrz funkcji `main`. Połączenie tego modułu z pierwszym modułem spowoduje wygenerowanie LNK4049 narzędzi KONSOLIDATORA. Usuń modyfikator `__declspec(dllimport)` z deklaracji, aby rozwiązać ten problem.

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

## <a name="see-also"></a>Zobacz też

[Ostrzeżenie narzędzi konsolidatora lnk4217 narzędzi konsolidatora](linker-tools-warning-lnk4217.md) \
[Ostrzeżenie narzędzi konsolidatora LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
