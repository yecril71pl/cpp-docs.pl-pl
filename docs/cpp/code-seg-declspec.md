---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: 22703e92b1a127378c965ce12bcc4e5475b3e452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180839"
---
# <a name="code_seg-__declspec"></a>code_seg (__declspec)

**Specyficzne dla firmy Microsoft**

Atrybut deklaracji **code_seg** nazwy wykonywalnego segmentu tekstu w pliku. obj, w którym będzie przechowywany kod obiektu funkcji lub funkcji składowych klasy.

## <a name="syntax"></a>Składnia

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Uwagi

Atrybut `__declspec(code_seg(...))` umożliwia rozmieszczenie kodu do oddzielnych segmentów nazwanych, które mogą być stronicowane lub blokowane w pamięci osobno. Możesz używać tego atrybutu, aby kontrolować rozmieszczenie wystąpień szablonów i kodu generowanego przez kompilator.

*Segment* to nazwany blok danych w pliku. obj, który jest ładowany do pamięci jako jednostka. *Segment tekstu* jest segmentem zawierającym kod wykonywalny. *Sekcja* termin jest często używana zamiennie z segmentem.

Kod obiektu, który jest generowany, gdy `declarator` jest zdefiniowany, jest umieszczany w segmencie tekstowym określonym przez `segname`, który jest literałem wąskim ciągiem. Nazwa `segname` nie musi być określona w [sekcji](../preprocessor/section.md) pragma, zanim będzie mogła zostać użyta w deklaracji. Domyślnie, gdy nie `code_seg` jest określony, kod obiektu jest umieszczany w segmencie o nazwie. Text. Atrybut **code_seg** zastępuje wszelkie istniejące [#pragma code_seg](../preprocessor/code-seg.md) dyrektywie. Atrybut **code_seg** stosowany do funkcji składowej przesłania dowolny atrybut **code_seg** zastosowany do otaczającej klasy.

Jeśli jednostka ma atrybut **code_seg** , wszystkie deklaracje i definicje tej samej jednostki muszą mieć identyczne atrybuty **code_seg** . Jeśli klasa podstawowa ma atrybut **code_seg** , klasy pochodne muszą mieć ten sam atrybut.

Gdy atrybut **code_seg** jest stosowany do funkcji zakresu przestrzeni nazw lub funkcji członkowskiej, kod obiektu dla tej funkcji jest umieszczany w określonym segmencie tekstu. Gdy ten atrybut jest stosowany do klasy, wszystkie funkcje składowych klasy i klas zagnieżdżonych — dotyczy to również generowanych przez kompilator specjalnych składowych funkcji — są umieszczane w określonym segmencie. Klasy zdefiniowane lokalnie — na przykład klasy zdefiniowane w treści funkcji składowej — nie dziedziczą atrybutu **code_seg** otaczającego zakresu.

Gdy atrybut **code_seg** jest stosowany do klasy szablonu lub funkcji szablonu, wszystkie niejawne specjalizacje szablonu są umieszczane w określonym segmencie. Jawne lub częściowe specjalizacje nie dziedziczą atrybutu **code_seg** z podstawowego szablonu. Możesz określić ten sam lub inny atrybut **code_seg** dla specjalizacji. Nie można zastosować atrybutu **code_seg** do jawnego tworzenia wystąpienia szablonu.

Domyślnie, kod generowany przez kompilator, taki jak funkcja specjalna elementu członkowskiego, jest umieszczany w segmencie .text. Dyrektywa `#pragma code_seg` nie przesłania tego ustawienia domyślnego. Użyj atrybutu **code_seg** dla klasy, szablonu klasy lub szablonu funkcji, aby kontrolować miejsce umieszczenia kodu generowanego przez kompilator.

Wyrażenia lambda dziedziczą atrybuty **code_seg** z ich zakresu otaczającego. Aby określić segment dla wyrażenia lambda, zastosuj atrybut **code_seg** po klauzuli deklaracji parametru i przed jakąkolwiek specyfikacją lub wyjątkami o typie zwracanym, wszelkie końcowe specyfikacje typu powrotu i treści lambda. Aby uzyskać więcej informacji, zobacz [składnia wyrażenia lambda](../cpp/lambda-expression-syntax.md). Ten przykład definiuje lambdę w segmencie o nazwie PagedMem:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Należy zachować ostrożność przy umieszczaniu określonych funkcji elementów członkowskich — zwłaszcza wirtualnych funkcji elementów członkowskich — w różnych segmentach. W przypadku definiowania funkcji wirtualnej w klasie pochodnej, która znajduje się w segmencie stronicowanym, gdy metoda klasy bazowej znajduje się w segmencie niestronicowanym, inne metody klasy bazowej lub kod użytkownika mogą przyjąć, że wywołanie wirtualnej metody nie wywoła błędu stronicowania.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak atrybut **code_seg** kontroluje umieszczanie segmentu w przypadku użycia niejawnej i jawnej specjalizacji szablonu:

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
