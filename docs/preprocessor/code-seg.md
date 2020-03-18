---
title: code_seg pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: 65d702273593dc7fba68cc040f700b01a2c5e4a7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446476"
---
# <a name="code_seg-pragma"></a>code_seg pragma

Określa sekcję tekstową (segment), w której funkcje są przechowywane w pliku obiektu (. obj).

## <a name="syntax"></a>Składnia

> **#pragma code_seg (** ["*Nazwa sekcji*" [ **,** "*Klasa sekcji*"]] **)** \
> **#pragma code_seg (** { **push** | **pop** } [ **,** *Identyfikator* ] [ **,** "*sekcja-Name*" [ **,** "*Section-Class*"]] **)**

### <a name="parameters"></a>Parametry

**wypychanie**\
Obowiązkowe Umieszcza rekord na wewnętrznym stosie kompilatora. **Wypchnięcie** może mieć *Identyfikator* i *nazwę sekcji*.

\ **pop**
Obowiązkowe Usuwa rekord z góry wewnętrznego stosu kompilatora. **Punkt obecności** może mieć *Identyfikator* i *nazwę sekcji*. Można wyskakujące wiele rekordów przy użyciu tylko jednego polecenia **pop** przy użyciu *identyfikatora*. *Nazwa sekcji* zmieni się na nazwę aktywnej sekcji tekstowej po punkcie pop.

*identyfikator*\
Obowiązkowe W przypadku użycia z opcją **push**przypisuje nazwę rekordu na wewnętrznym stosie kompilatora. Gdy jest używany z **pop**, dyrektywa pop rejestruje wewnętrzny stos do momentu usunięcia *identyfikatora* . Jeśli na stosie wewnętrznym nie znaleziono *identyfikatora* , nic nie jest zdjęte.

"*Nazwa sekcji*" \
Obowiązkowe Nazwa sekcji. Gdy jest używany z **punktem pop**, stos jest zdjęte, a *sekcja Name* to nazwa aktywnej sekcji tekstowej.

"*Klasa sekcji*" \
Obowiązkowe Zignorowano, ale uwzględniono zgodność z wersjami C++ firmy Microsoft wcześniejszą niż wersja 2,0.

## <a name="remarks"></a>Uwagi

*Sekcja* w pliku obiektu to nazwany blok danych, który jest ładowany do pamięci jako jednostka. *Sekcja tekstowa* to Sekcja zawierająca kod wykonywalny. W tym artykule, *segment* i *sekcja* terminów mają takie samo znaczenie.

Dyrektywa dyrektywy pragma **code_seg** poleca kompilatorowi umieszczenie wszystkich kolejnych kodów obiektów z jednostki tłumaczenia do sekcji tekstowej o nazwie *sekcja-Name*. Domyślnie sekcja tekstowa używana dla funkcji w pliku obiektu ma nazwę `.text`. Dyrektywa pragma **code_seg** , bez parametru *Section Name* resetuje nazwę sekcji tekst dla kolejnego kodu obiektu do `.text`.

Dyrektywa pragma **code_seg** nie kontroluje umieszczania kodu obiektu wygenerowanego dla szablonów wystąpień. Ani nie kontroluje kodu wygenerowanego niejawnie przez kompilator, takiego jak specjalne funkcje składowe. Aby kontrolować ten kod, zalecamy użycie zamiast niego atrybutu [__declspec (code_seg (...))](../cpp/code-seg-declspec.md) . Zapewnia kontrolę nad umieszczaniem wszystkich kodów obiektów, w tym kodu wygenerowanego przez kompilator.

Aby uzyskać listę nazw, które nie powinny być używane do tworzenia sekcji, zobacz [/Section](../build/reference/section-specify-section-attributes.md).

Można również określić sekcje dla zainicjowanych danych ([data_seg](../preprocessor/data-seg.md)), niezainicjowane dane ([bss_seg](../preprocessor/bss-seg.md)) i zmienne const ([const_seg](../preprocessor/const-seg.md)).

Możesz użyć [polecenia DUMPBIN. Aplikacja EXE](../build/reference/dumpbin-command-line.md) do wyświetlania plików obiektów. Wersje programu polecenia DUMPBIN dla każdej obsługiwanej architektury docelowej są dołączone do programu Visual Studio.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak używać dyrektywy pragma **code_seg** w celu kontrolowania miejsca, w którym jest umieszczany kod obiektu:

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>Zobacz też

[code_seg (__declspec)](../cpp/code-seg-declspec.md)\
[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
