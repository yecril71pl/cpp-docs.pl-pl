---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: a0b9c6dcd7ee19af59ac39a71498fe41bfc107ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216557"
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)

**Microsoft Specific**

**Code_seg** deklaracji atrybutu nazywa wykonywalny segment tekstu w pliku .obj, w którym będą przechowywane kod obiektu dla funkcji lub funkcje składowych klasy.

## <a name="syntax"></a>Składnia

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Uwagi

`__declspec(code_seg(...))` Atrybut umożliwia umieszczanie kodu w oddzielnych segmentach, które mogą być stronicowane lub zablokowane w pamięci indywidualnie. Możesz używać tego atrybutu, aby kontrolować rozmieszczenie wystąpień szablonów i kodu generowanego przez kompilator.

A *segmentu* to nazwany blok danych w pliku .obj, który jest ładowany do pamięci jako jednostka. A *segment tekstu* to segment, który zawiera kod wykonywalny. Termin *sekcji* jest używany zamiennie z terminem segment.

Kod obiektowy, który został wygenerowany, gdy `declarator` jest definiowany jest umieszczany w segmencie tekstu określonym przez `segname`, który jest literałem ciągu wąskiego. Nazwa `segname` nie musi być określona w [sekcji](../preprocessor/section.md) pragma, zanim będzie można używać w deklaracji. Domyślnie, gdy nie `code_seg` jest określony, kod obiektowy jest umieszczany w segmencie o nazwie .text. A **code_seg** atrybut zastępuje wszelkie istniejące [#pragma code_seg](../preprocessor/code-seg.md) dyrektywy. A **code_seg** zastosowany do funkcji składowej zastępuje dowolny **code_seg** zastosowany do klasy otaczającej.

Jeśli jednostka ma **code_seg** atrybutu, wszystkie deklaracje i definicje tego samego obiektu muszą mieć identyczne **code_seg** atrybutów. Jeśli klasa podstawowa ma **code_seg** atrybutu pochodne klasy muszą mieć ten sam atrybut.

Gdy **code_seg** atrybut jest stosowany do funkcji zakresu przestrzeni nazw lub funkcji elementu członkowskiego, kod obiektowy dla tej funkcji jest umieszczany w określonym segmencie tekstu. Gdy ten atrybut jest stosowany do klasy, wszystkie funkcje składowych klasy i klas zagnieżdżonych — dotyczy to również generowanych przez kompilator specjalnych składowych funkcji — są umieszczane w określonym segmencie. Lokalnie zdefiniowane klasy — na przykład klasy zdefiniowane w treści funkcji składowej — nie dziedziczą **code_seg** atrybut otaczającego zakresu.

Gdy **code_seg** atrybut jest stosowany do szablonu klasy lub funkcji szablonu, wszystkie niejawne specjalizacje szablonu są umieszczane w określonym segmencie. Jawne lub częściowe specjalizacje nie dziedziczą **code_seg** atrybutu z szablonu podstawowego. Użytkownik może określić tego samego lub innego **code_seg** atrybutu dla specjalizacji. A **code_seg** atrybutu nie można zastosować do jawnego wystąpienia szablonu.

Domyślnie, kod generowany przez kompilator, taki jak funkcja specjalna elementu członkowskiego, jest umieszczany w segmencie .text. `#pragma code_seg` Dyrektywy nie zastąpić to ustawienie domyślne. Użyj **code_seg** atrybutu dla klasy, szablonu klasy lub szablonu funkcji do kontroli, gdzie jest umieścić kod wygenerowany przez kompilator.

Lambdy dziedziczą **code_seg** atrybuty z ich obejmującego zakresu. Aby określić segment dla lambdy, zastosuj **code_seg** atrybutu po klauzuli deklaracji parametru i przed jakąkolwiek mutable lub specyfikacja wyjątku, wszelkie końcową specyfikacją typu zwracanego i treść lambda. Aby uzyskać więcej informacji, zobacz [Lambda Expression Syntax](../cpp/lambda-expression-syntax.md). Ten przykład definiuje lambdę w segmencie o nazwie PagedMem:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Należy zachować ostrożność przy umieszczaniu określonych funkcji elementów członkowskich — zwłaszcza wirtualnych funkcji elementów członkowskich — w różnych segmentach. W przypadku definiowania funkcji wirtualnej w klasie pochodnej, która znajduje się w segmencie stronicowanym, gdy metoda klasy bazowej znajduje się w segmencie niestronicowanym, inne metody klasy bazowej lub kod użytkownika mogą przyjąć, że wywołanie wirtualnej metody nie wywoła błędu stronicowania.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak **code_seg** atrybutu formanty umieszczenie segmentu, gdy niejawne i specjalizacji jawnego szablonu jest używany:

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)