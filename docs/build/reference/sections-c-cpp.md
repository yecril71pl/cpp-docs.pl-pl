---
title: SEKCJE (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecd8d6050df7a4d30b0a37cad28e030d1cd63cf0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722901"
---
# <a name="sections-cc"></a>SEKCJE (C/C++)

Wprowadza części w co najmniej jednego `definitions` , które są specyfikatory dostępu, w sekcji w pliku danych wyjściowych projektu.

```
SECTIONS
definitions
```

## <a name="remarks"></a>Uwagi

Każda definicja musi być w oddzielnym wierszu. `SECTIONS` — Słowo kluczowe może być na tym samym wierszu co pierwsza definicja lub na poprzedni wiersz. Plik .def może zawierać jeden lub więcej `SECTIONS` instrukcji.

To `SECTIONS` instrukcja Ustawia atrybuty dla jednej lub więcej sekcji w pliku obrazu i może służyć do zastępowania atrybutów domyślnych dla każdego typu sekcji.

Format `definitions` jest:

`.section_name specifier`

gdzie `.section_name` to nazwa sekcji w obrazie programu i `specifier` jest co najmniej następujące modyfikatory dostępu:

|Modyfikator|Opis|
|--------------|-----------------|
|`EXECUTE`|Sekcja jest wykonywalny|
|`READ`|Zezwala na operacje odczytu danych|
|`SHARED`|Udostępnia sekcji między wszystkie procesy, które ładują obrazu|
|`WRITE`|Umożliwia wykonywanie operacji zapisu na danych|

Specyfikator nazwy należy oddzielić spacjami. Na przykład:

```
SECTIONS
.rdata READ WRITE
```

`SECTIONS` oznacza początek listy sekcji `definitions`. Każdy `definition` muszą znajdować się w osobnym wierszu. `SECTIONS` — Słowo kluczowe może być w tym samym wierszu jako pierwsze `definition` lub na poprzedni wiersz. Plik .def może zawierać jeden lub więcej `SECTIONS` instrukcji. `SEGMENTS` — Słowo kluczowe jest obsługiwany jako synonim dla `SECTIONS`.

Starsze wersje programu Visual C++ są obsługiwane:

```
section [CLASS 'classname'] specifier
```

`CLASS` — Słowo kluczowe jest obsługiwana w przypadku zgodności, ale został zignorowany.

Jest równoważne sposób Określ atrybuty sekcji [/SECTION](../../build/reference/section-specify-section-attributes.md) opcji.

## <a name="see-also"></a>Zobacz też

[Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)