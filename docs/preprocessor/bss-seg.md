---
title: bss_seg
ms.date: 10/22/2018
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: 489ced11bb6024fdf9818872c07ab7feebfeabf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212418"
---
# <a name="bssseg"></a>bss_seg

Określa segment, w którym niezainicjowane zmienne są przechowywane w pliku .obj.

## <a name="syntax"></a>Składnia

```
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parametry

**push**<br/>
(Opcjonalnie) Umieszcza rekord na wewnętrznym stosie kompilatora. A *pu*sh * może mieć *identyfikator* i *nazwą segmentu*.

**POP**<br/>
(Opcjonalnie) Usuwa rekord z góry wewnętrznego stosu kompilatora.

*Identyfikator*<br/>
(Opcjonalnie) Gdy jest używane z **wypychania**, przypisuje nazwę rekordowi na wewnętrznym stosie kompilatora. *Identyfikator* umożliwia wielu rekordów zostać zdjęte ze stosu za pomocą jednego **pop** polecenia. Gdy jest używane z **pop**, dyrektywa zdejmuje rekordy z wewnętrznego stosu aż do usunięcia *identyfikator* zostanie usunięta; Jeśli *identyfikator* nie zostanie znaleziony na wewnętrznym stosie, nic nie zdjęte ze stosu.

*"segment-name"*<br/>
(Opcjonalnie) Nazwa segmentu. Gdy jest używane z **pop**, stos jest zdejmowany i *nazwą segmentu* staje się nazwą aktywny segment.

*"segment-class"*<br/>
(Opcjonalnie) Uwzględnione na potrzeby utrzymywania zgodności z C++ wcześniejszych niż 2.0. Jest on ignorowany.

## <a name="remarks"></a>Uwagi

. Pliki obj mogą być wyświetlane z [dumpbin](../build/reference/dumpbin-command-line.md) aplikacji. Segment domyślnej w pliku .obj, niezainicjowanych danych jest .bss. W niektórych przypadkach użycie **bss_seg** można przyspieszyć czasów ładowania przez grupowanie niezainicjowanych danych w jednej sekcji.

**bss_seg** bez parametrów resetuje segmentu .bss.

Danych przydzielonych przy użyciu **bss_seg** pragma nie zachowuje żadnych informacji o lokalizacji.

Można również określić sekcje dla danych zainicjowanych ([data_seg](../preprocessor/data-seg.md)), funkcje ([code_seg](../preprocessor/code-seg.md)) i zmiennych const ([const_seg](../preprocessor/const-seg.md)).

Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) listę nazw, nie należy używać podczas tworzenia sekcji.

## <a name="example"></a>Przykład

```cpp
// pragma_directive_bss_seg.cpp
int i;                     // stored in .bss
#pragma bss_seg(".my_data1")
int j;                     // stored in .my_data1

#pragma bss_seg(push, stack1, ".my_data2")
int l;                     // stored in .my_data2

#pragma bss_seg(pop, stack1)   // pop stack1 from stack
int m;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
