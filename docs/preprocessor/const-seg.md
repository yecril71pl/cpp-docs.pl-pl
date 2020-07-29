---
title: const_seg, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: 04467df1205bd6d4c70687422572aef898d46f68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231627"
---
# <a name="const_seg-pragma"></a>const_seg, pragma

Określa sekcję (segment), gdzie zmienne [const](../cpp/const-cpp.md) są przechowywane w pliku obiektu (. obj).

## <a name="syntax"></a>Składnia

> **#pragma const_seg (** ["*Nazwa sekcji*" [ **,** "*Klasa sekcji*"]] **)**\
> **#pragma const_seg (** { **push**  |  **pop** } [ **,** *Identyfikator* ] [ **,** "*sekcja-Name*" [ **,** "*Section-Class*"]] **)**

### <a name="parameters"></a>Parametry

**wydajności**\
Obowiązkowe Umieszcza rekord na wewnętrznym stosie kompilatora. **Wypchnięcie** może mieć *Identyfikator* i *nazwę sekcji*.

**skakując**\
Obowiązkowe Usuwa rekord z góry wewnętrznego stosu kompilatora. **Punkt obecności** może mieć *Identyfikator* i *nazwę sekcji*. Można wyskakujące wiele rekordów przy użyciu tylko jednego polecenia **pop** przy użyciu *identyfikatora*. *Nazwa sekcji* zmieni się na nazwę aktywnej stałej sekcji po punkcie pop.

*identyfikatora*\
Obowiązkowe W przypadku użycia z opcją **push**przypisuje nazwę rekordu na wewnętrznym stosie kompilatora. Gdy jest używany z **pop**, dyrektywa pop rejestruje wewnętrzny stos do momentu usunięcia *identyfikatora* . Jeśli na stosie wewnętrznym nie znaleziono *identyfikatora* , nic nie jest zdjęte.

"*Nazwa sekcji*" \
Obowiązkowe Nazwa sekcji. Gdy jest używany z **punktem obecności**, stos jest zdjęte, a *sekcja Name* to nazwa sekcji aktywnej stałej.

"*Klasa sekcji*" \
Obowiązkowe Ignorowany, ale dołączono do zgodności z wersjami Microsoft C++ wcześniejszymi niż wersja 2,0.

## <a name="remarks"></a>Uwagi

*Sekcja* w pliku obiektu to nazwany blok danych, który jest ładowany do pamięci jako jednostka. *Sekcja const* to Sekcja zawierająca dane stałe. W tym artykule, *segment* i *sekcja* terminów mają takie samo znaczenie.

Dyrektywa dyrektywy pragma **const_seg** poleca kompilatorowi umieszczenie wszystkich stałych elementów danych z jednostki translacji w sekcji const o nazwie *sekcja-Name*. Sekcja domyślna w pliku obiektu dla **`const`** zmiennych to `.rdata` . Niektóre **`const`** zmienne, takie jak skalarne, są automatycznie podkreślane w strumieniu kodu. Kod z konturem nie jest wyświetlany w `.rdata` . Dyrektywa pragma **const_seg** , bez parametru *Section Name* resetuje nazwę sekcji dla kolejnych **`const`** elementów danych do `.rdata` .

Jeśli zdefiniujesz obiekt, który wymaga inicjalizacji dynamicznej w `const_seg` , wynik jest niezdefiniowanym zachowaniem.

Aby uzyskać listę nazw, które nie powinny być używane do tworzenia sekcji, zobacz [/Section](../build/reference/section-specify-section-attributes.md).

Można także określić sekcje dla zainicjowanych danych ([data_seg](../preprocessor/data-seg.md)), niezainicjowane dane ([bss_seg](../preprocessor/bss-seg.md)) i funkcje ([code_seg](../preprocessor/code-seg.md)).

Aplikacja [DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) służy do wyświetlania plików obiektów. Wersje programu polecenia DUMPBIN dla każdej obsługiwanej architektury docelowej są dołączone do programu Visual Studio.

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

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
