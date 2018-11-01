---
title: Błąd narzędzi konsolidatora LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: e55202274c5ec3982f784ad6cdf074a5a99e922f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491393"
---
# <a name="linker-tools-error-lnk2022"></a>Błąd narzędzi konsolidatora LNK2022

> Operacja metadanych nie powiodła się (*HRESULT*): *error_message*

Konsolidator wykrył błąd podczas scalania metadanych. Błędów metadanych muszą zostać rozwiązane, aby połączyć się pomyślnie.

Jednym ze sposobów, aby zdiagnozować ten problem jest uruchomienie **ildasm — tokeny** plików obiektu, aby dowiedzieć się, jakie typy mają tokenów na liście `error_message`i poszukaj różnice.  W metadanych dwa różne typy o takiej samej nazwie jest nieprawidłowy, nawet jeśli po prostu atrybut element LayoutType różni się.

Jeden przyczyny LNK2022 jest typem (na przykład struktury) istnieje w wielu compilands o takiej samej nazwie, ale z definicjami powodujące konflikt, i kiedy kompilujesz z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  W takim przypadku upewnij się, że typ ma identyczne definicję w compilands wszystkich.  Nazwa typu jest wyświetlana w `error_message`.

Inną możliwą przyczyną LNK2022 jest, jeśli konsolidator znajdzie plik metadanych w innej lokalizacji niż określono w kompilatorze (przy użyciu [#using](../../preprocessor/hash-using-directive-cpp.md) ). Upewnij się, że plik metadanych (.dll lub moduł .netmodule) jest w tej samej lokalizacji, gdy przekazywane do konsolidatora, jak w momencie został przekazany do kompilatora.

Podczas tworzenia aplikacji biblioteki ATL, użyj makra `_ATL_MIXED` jest wymagany w wszystkich compilands, jeśli jest on używany w co najmniej jednym.

## <a name="example"></a>Przykład

Poniższy przykład definiuje typ puste.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>Przykład

Niniejszy przykład pokazuje, że nie można połączyć dwa pliki kodu źródłowego, zawierających typy o takiej samej nazwie, ale różnych definicjach.

Poniższy przykład spowoduje wygenerowanie LNK2022.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```