---
title: code_seg (__declspec) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- code_seg_cpp
dev_langs:
- C++
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae69cd9e88b97a31dda86648d86e143ab9bd5d40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)
**Dotyczące firmy Microsoft**  
  
 `code_seg` Deklaracji atrybutu nazwy segment pliku wykonywalnego tekst w pliku .obj, w którym będzie przechowywany kod obiektu funkcja lub funkcje elementu członkowskiego klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(code_seg("segname")) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 `__declspec(code_seg(...))` Atrybut umożliwia umieszczanie kodu w oddzielnym o nazwie segmentów, które mogą być stronicowana lub zablokowane indywidualnie w pamięci. Możesz używać tego atrybutu, aby kontrolować rozmieszczenie wystąpień szablonów i kodu generowanego przez kompilator.  
  
 A *segmentu* jest nazwane bloku danych w pliku .obj, który jest ładowany do pamięci jako jednostka. A *segment tekstu* jest segment, który zawiera kod wykonywalny. Termin *sekcji* jest często używane zamiennie z segmentem.  
  
 Kod, który został wygenerowany, gdy obiekt `declarator` jest zdefiniowany jest umieszczany w segmencie tekstu określonego przez `segname`, który jest literałem wąski ciąg. Nazwa `segname` nie muszą być określone w [sekcji](../preprocessor/section.md) pragma, zanim będzie można użyć w deklaracji. Domyślnie, gdy nie `code_seg` określono kod obiektu jest umieszczany w segmencie o nazwie .text. A `code_seg` atrybutu zastępuje ewentualny istniejący [#pragma code_seg](../preprocessor/code-seg.md) dyrektywy. A `code_seg` atrybut zastosowany do funkcji członkowskiej zastępuje wszelkie `code_seg` atrybutem stosowanym do klasy otaczającej.  
  
 Jeśli jednostka ma `code_seg` atrybutu wszystkie deklaracje i definicje tej samej jednostki muszą mieć identyczne `code_seg` atrybutów. Jeśli klasa podstawowa ma `code_seg` atrybutu pochodnego klas muszą być tego samego atrybutu.  
  
 Gdy `code_seg` atrybut jest stosowany dla funkcji zakresie przestrzeni nazw lub funkcji członkowskiej, kod obiektu dla tej funkcji jest umieszczany w segmencie określony tekst. Gdy ten atrybut jest stosowany do klasy, wszystkie funkcje składowych klasy i klas zagnieżdżonych — dotyczy to również generowanych przez kompilator specjalnych składowych funkcji — są umieszczane w określonym segmencie. Lokalnie zdefiniowany klasy — na przykład klas zdefiniowanych w treści funkcji Członkowskich — nie dziedziczą `code_seg` atrybutu otaczającego zakresu.  
  
 Gdy `code_seg` atrybut jest stosowany do szablonu klasy lub szablonu funkcji, wszystkie niejawne specjalizacji szablonu są umieszczane w określony segment. Jawna lub częściowa specjalizacje nie dziedziczą `code_seg` atrybut z szablonu podstawowego. Można określić tej samej lub innej `code_seg` atrybutu w specjalizacji. A `code_seg` atrybutu nie można zastosować do wystąpienia jawnego szablonu.  
  
 Domyślnie, kod generowany przez kompilator, taki jak funkcja specjalna elementu członkowskiego, jest umieszczany w segmencie .text. `#pragma code_seg` Dyrektywy nie zastąpić to ustawienie domyślne. Użyj `code_seg` atrybutu klasy, szablon klasy lub szablonu funkcji do kontroli, którym jest umieszczany kod wygenerowany przez kompilator.  
  
 Wyrażenia lambda dziedziczą `code_seg` atrybutów z ich otaczającego zakresu. Aby określić segment dla wyrażenia lambda, zastosuj `code_seg` atrybutu po klauzuli deklaracji parametru i przed każdą modyfikowalną lub specyfikacji wyjątku, wszelkich końcowych specyfikacji zwracanego typu i treści lambda. Aby uzyskać więcej informacji, zobacz [składnia wyrażenia Lambda](../cpp/lambda-expression-syntax.md). Ten przykład definiuje lambdę w segmencie o nazwie PagedMem:  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 Należy zachować ostrożność przy umieszczaniu określonych funkcji elementów członkowskich — zwłaszcza wirtualnych funkcji elementów członkowskich — w różnych segmentach. W przypadku definiowania funkcji wirtualnej w klasie pochodnej, która znajduje się w segmencie stronicowanym, gdy metoda klasy bazowej znajduje się w segmencie niestronicowanym, inne metody klasy bazowej lub kod użytkownika mogą przyjąć, że wywołanie wirtualnej metody nie wywoła błędu stronicowania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano sposób `code_seg` formanty atrybutu segment umieszczania podczas niejawnego i jawnego szablonu specjalizacji jest używany:  
  
```  
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
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)