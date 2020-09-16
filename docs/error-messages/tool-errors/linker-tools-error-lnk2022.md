---
title: Błąd narzędzi konsolidatora LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: 187a63cb4bd22fc5e0d35523d97f438ba56b8576
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686361"
---
# <a name="linker-tools-error-lnk2022"></a>Błąd narzędzi konsolidatora LNK2022

> Operacja metadanych nie powiodła się (*HRESULT*): *ERROR_MESSAGE*

Konsolidator wykrył błąd podczas scalania metadanych. Błędy metadanych muszą zostać rozwiązane, aby można było pomyślnie połączyć.

Jednym ze sposobów zdiagnozowania tego problemu jest uruchomienie **Ildasm-Tokens** w plikach obiektów, aby znaleźć typy, w których znajdują się tokeny `error_message` , i poszukać różnic.  W metadanych dwa różne typy o tej samej nazwie są nieprawidłowe, nawet jeśli atrybut tylko LayoutType jest inny.

Jedną z przyczyn LNK2022 jest to, że typ (taki jak struktura) istnieje w wielu compilandsach o tej samej nazwie, ale z definicjami powodującymi konflikt i w przypadku kompilowania z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  W tym przypadku upewnij się, że typ ma identyczną definicję we wszystkich compilands.  Nazwa typu jest wymieniona w `error_message` .

Kolejną możliwą przyczyną LNK2022 jest to, że konsolidator odnajdzie plik metadanych w innej lokalizacji niż został określony w kompilatorze (z [#using](../../preprocessor/hash-using-directive-cpp.md) ). Upewnij się, że plik metadanych (. dll lub. module) znajduje się w tej samej lokalizacji podczas przekazywania do konsolidatora, ponieważ był on przekazano do kompilatora.

Podczas kompilowania aplikacji ATL, użycie makra `_ATL_MIXED` jest wymagane we wszystkich compilands, jeśli jest używany w co najmniej jednym.

## <a name="examples"></a>Przykłady

Poniższy przykład definiuje pusty typ.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

Ten przykład pokazuje, że nie można połączyć dwóch plików kodu źródłowego, które zawierają typy o takiej samej nazwie, ale różne definicje.

Poniższy przykład generuje LNK2022.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```
