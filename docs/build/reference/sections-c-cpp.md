---
title: SEKCJE (C/C++)
ms.date: 11/04/2016
f1_keywords:
- SECTIONS
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
ms.openlocfilehash: 5125b09675969c784aafe375faf1fdbc36d8c5d9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815115"
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

Jest równoważne sposób Określ atrybuty sekcji [/SECTION](section-specify-section-attributes.md) opcji.

## <a name="see-also"></a>Zobacz także

[Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)
