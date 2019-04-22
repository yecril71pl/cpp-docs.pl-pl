---
title: const_seg
ms.date: 09/17/2018
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: c58f154f5e1ab6906b45d59f454a7dc2b5c0bfbe
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029625"
---
# <a name="constseg"></a>const_seg
Określa segment gdzie [const](../cpp/const-cpp.md) zmienne są przechowywane w pliku .obj.

## <a name="syntax"></a>Składnia

```
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parametry

**push**<br/>
(Opcjonalnie) Umieszcza rekord na wewnętrznym stosie kompilatora. A **wypychania** może mieć *identyfikator* i *nazwą segmentu*.

**POP**<br/>
(Opcjonalnie) Usuwa rekord z góry wewnętrznego stosu kompilatora.

*Identyfikator*<br/>
(Opcjonalnie) Gdy jest używane z **wypychania**, przypisuje nazwę rekordowi na wewnętrznym stosie kompilatora. Gdy jest używane z **pop**, zdejmuje rekordy z wewnętrznego stosu aż do usunięcia *identyfikator* zostanie usunięta; Jeśli *identyfikator* nie zostanie znaleziony na wewnętrznym stosie, nic nie zostanie zdjęte.

Za pomocą *identyfikator* umożliwia wielu rekordów zostać zdjęte ze stosu za pomocą jednego **pop** polecenia.

"*nazwą segmentu*"<br/>
(Opcjonalnie) Nazwa segmentu. Gdy jest używane z **pop**, stos jest zdejmowany i *nazwą segmentu* staje się nazwą aktywny segment.

"*klasy segmentu*"<br/>
(Opcjonalnie) Uwzględnione na potrzeby utrzymywania zgodności z C++ wcześniejszych niż 2.0. Jest on ignorowany.

## <a name="remarks"></a>Uwagi

Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.

Pliki OBJ mogą być wyświetlane z [dumpbin](../build/reference/dumpbin-command-line.md) aplikacji. Segment domyślnej w pliku .obj `const` zmiennych jest .rdata. Niektóre `const` zmienne, takie jak wartości skalarnych, są automatycznie śródwierszowe w strumieniu kodu. Śródwierszowe kodu nie będą widoczne w .rdata.

Definiowanie obiektu wymagające dynamiczna Inicjalizacja w `const_seg` powoduje zachowanie niezdefiniowane.

`#pragma const_seg` bez parametrów resetuje segmentu .rdata.

## <a name="example"></a>Przykład

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="comments"></a>Komentarze

Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) listę nazw, nie należy używać podczas tworzenia sekcji.

Można również określić sekcje dla danych zainicjowanych ([data_seg](../preprocessor/data-seg.md)), niezainicjowanych danych ([bss_seg](../preprocessor/bss-seg.md)) i funkcje ([code_seg](../preprocessor/code-seg.md)).

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)