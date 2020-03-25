---
title: Błąd narzędzi konsolidatora LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: d30dad6f8ad146ff467eb4eaf32b21dd6950d25f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194645"
---
# <a name="linker-tools-error-lnk2022"></a>Błąd narzędzi konsolidatora LNK2022

> Operacja metadanych nie powiodła się (*HRESULT*): *ERROR_MESSAGE*

Konsolidator wykrył błąd podczas scalania metadanych. Błędy metadanych muszą zostać rozwiązane, aby można było pomyślnie połączyć.

Jednym ze sposobów zdiagnozowania tego problemu jest uruchomienie **Ildasm tokenów** w plikach obiektów w celu znalezienia, które typy mają tokeny wymienione w `error_message`, i poszukaj różnic.  W metadanych dwa różne typy o tej samej nazwie są nieprawidłowe, nawet jeśli atrybut tylko LayoutType jest inny.

Jedną z przyczyn LNK2022 jest to, że typ (taki jak struktura) istnieje w wielu compilandsach o tej samej nazwie, ale z definicjami powodującymi konflikt i w przypadku kompilowania z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  W tym przypadku upewnij się, że typ ma identyczną definicję we wszystkich compilands.  Nazwa typu jest wymieniona w `error_message`.

Kolejną możliwą przyczyną LNK2022 jest to, że konsolidator odnajdzie plik metadanych w innej lokalizacji niż został określony w kompilatorze (z [#using](../../preprocessor/hash-using-directive-cpp.md) ). Upewnij się, że plik metadanych (. dll lub. module) znajduje się w tej samej lokalizacji podczas przekazywania do konsolidatora, ponieważ był on przekazano do kompilatora.

Podczas kompilowania aplikacji ATL, użycie makra `_ATL_MIXED` jest wymagane we wszystkich compilandsach, jeśli jest używany w co najmniej jednym.

## <a name="example"></a>Przykład

Poniższy przykład definiuje pusty typ.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>Przykład

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
