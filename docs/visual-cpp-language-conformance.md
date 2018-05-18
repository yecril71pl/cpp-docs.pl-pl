---
title: Zgodność języka Visual C++ | Dokumentacja firmy Microsoft
ms.date: 11/15/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70fc4705b6e150978812563fcde9e0f4d6b3cea1
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="visual-c-language-conformance"></a>Zgodność języka Visual C++

Ten temat zawiera podsumowanie ISO języka C ++ 03, C ++ 11, języka C ++ 14, C ++ 17 i projekt C ++ 20 standardów zgodność języka funkcji kompilatora i funkcje standardowej biblioteki dla kompilatora języka C++ w programie Visual Studio 2017 i wcześniejszych wersjach. Każdego kompilatora i biblioteki standardowej funkcji nazwę łącza do dokumentacji propozycji standardowi ISO C++ zawiera opis funkcji, jeśli jest dostępny w momencie publikacji. Kolumna obsługiwane zawiera listę wersji programu Visual Studio, w których dla funkcji najpierw pojawił się.

Aby uzyskać więcej informacji na temat udoskonaleń zgodność i innych zmian wprowadzonych w programie Visual Studio 2017, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md) i [nowości w języku Visual C++ w programie Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md). Zgodność zmiany w starszych wersjach, zobacz [historii zmian Visual C++](porting/visual-cpp-change-history-2003-2015.md) i [Visual C++ co przez nowy 2003 za pośrednictwem 2015](porting/visual-cpp-what-s-new-2003-through-2015.md). Aby bieżące informacje od zespołu C++, odwiedź [blogu zespołu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

> [!NOTE]
> Nie ma żadnych danych binarnych fundamentalne zmiany między Visual Studio 2015 i Visual Studio 2017 r.

## <a name="compiler-features"></a>Funkcje kompilatora

|Obszar funkcji| |
|----|---|
|__C ++ 03/11 podstawowe języka funkcje__|__Obsługiwane__|
|&nbsp;&nbsp;Wszystkie inne|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;Wyszukiwanie nazwy dwufazowego|VS 2017 15.7 <sup> [B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 Wyrażenie techniki SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[C99 N1653 preprocesora](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Częściowe <sup> [D](#note_D)</sup>|
|&nbsp;&nbsp;[Rozszerzony N1988 typów całkowitych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|BRAK <sup> [E](#note_E)</sup>|
|__C ++ 14 podstawowe języka funkcje__|__Obsługiwane__|
|&nbsp;&nbsp;[N3323 Tweaked sformułowanie kontekstowej konwersji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[Literały N3472 binarne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[Automatycznie N3638 i decltype(auto) typy zwracane](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init przechwytywania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 ogólne wyrażenia lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[Atrybut N3760 [[przestarzały]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[Dezalokacja N3778 o rozmiarze](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[Separatory cyfr N3781](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[Szablony N3651 zmiennej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[Rozszerzony N3652 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[NSDMIs N3653 dla wartości zagregowanych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 Elementem zespalając zapobieganie/ze alokacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|BRAK <sup> [F](#note_F)</sup>|
|__C ++ 17 podstawowe języka funkcje__|__Obsługiwane__|
|&nbsp;&nbsp;[Usuwanie N4086 trigramów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 nowe zasady automatycznego przy nawiasach init list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Właściwość typename N4051 w parametrów szablonu szablonu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Atrybuty N4266 dla obszarów nazw i moduły wyliczające](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Literały znaków u8 N4267](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Zagnieżdżone N4230 definicji przestrzeni nazw](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 zwięzłym static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Uogólniony P0184R0 opartej na zakresie dla pętle](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 atrybutu [[przepuszczająca]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 usuwanie rejestru — słowo kluczowe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Usuwanie P0002R1 operator ++ na bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Przechwytywanie P0018R3 * to przez wartość](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 przy użyciu atrybutu przestrzeni nazw bez powtarzania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|2017 VS 15 USTĘP 3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 bezpośrednio listy inicjowania typów stałych wyliczeniowych z liczb całkowitych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Wyrażenia lambda constexpr P0170R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 atrybutu [[nodiscard]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 atrybutu [[maybe_unused]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Powiązania P0217R3 strukturalnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Jeśli constexpr P0292R2 — instrukcje](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|2017 VS 15 USTĘP 3 <sup> [G](#note_G)</sup>|
|&nbsp;&nbsp;[Instrukcje wyboru P0305R1 z inicjatorami](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Literały P0245R1 Hexfloat](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Stosowanie N4268 więcej argumentów szablonu bez typu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 Fold wyrażenia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Usuwanie P0003R5 dynamicznie-— specyfikacje wyjątków](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Dodawanie P0012R1 noexcept do typu systemu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 nadmiernie wyrównany dynamicznej alokacji pamięci](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zmienne wbudowane P0386R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Dopasowywanie P0522R0 szablonu — parametry szablonu do argumentów zgodne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Usuwanie P0036R0 niektóre pusta jednoargumentowy złożeń](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Konwersje ustalania N4261 kwalifikacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Rozszerzony P0017R1 inicjowania agregacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Wnioskowanie argumentu szablonu P0091R3 dla szablonów klas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[Problemy Wnioskowanie argumentu szablonu klasy P0512R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Deklarowanie P0127R2 parametrów szablonu bez typu z automatycznego](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Gwarantowane P0135R1 elision kopiowania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|2017 VS 15,6<sup>[H](#note_H)</sup>|
|&nbsp;&nbsp;[Zmieniając P0136R1 konstruktory dziedziczące](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Uściślenie P0145R3 kolejność obliczania wyrażenia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 kolejność obliczania argumentów funkcji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Rozszerzenia P0195R2 pakietów w deklaracje using](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Ignorowanie P0283R2 nierozpoznany atrybutów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0702R1 ustalania klasy Wnioskowanie argumentu szablonu dla konstruktorami listy inicjatorów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0702r1.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|

  
  
|Obszar funkcji| |
|----|---|
|__C ++ 17 podstawowe języka funkcji (usterką raportów)__|__Obsługiwane__|
|&nbsp;&nbsp;[P0702R1 ustalania klasy Wnioskowanie argumentu szablonu dla konstruktorami listy inicjatorów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0702r1.html)|VS 2017 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Upraszczanie P0588R1 lambda niejawne przechwytywania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|Nie|
|&nbsp;&nbsp;[CWG 1581: Gdy constexpr funkcji członkowskich zdefiniowanych?](https://wg21.cmeerw.net/cwg/issue1581)|Nie|
|&nbsp;&nbsp;[P0962R1 mniejsze powiązania structured dostosowania punktu znajdowanie reguły](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|Nie|
|&nbsp;&nbsp;[Zakres mniejsze P0962R2 — znajdowanie reguły punktu dostosowania pętli](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|Nie|
|&nbsp;&nbsp;[Stosowanie P0969R0 strukturę powiązania z dostępnych elementów członkowskich](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|Nie|

  
  
|Obszar funkcji| |
|----|---|
|__Funkcje języka 20 podstawowe języka c ++__|__Obsługiwane__|
|&nbsp;&nbsp;[Dodawanie P0306R4 &#95; &#95;VA_OPT&#95; &#95; pominięcie przecinkami i usuwania przecinkami](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0306r4.pdf)|Nie|
|&nbsp;&nbsp;[Inicjowanie wyznaczony P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|Nie|
|&nbsp;&nbsp;[Stosowanie P0409R2 lambda przechwytywania [=, to]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|Nie|
|&nbsp;&nbsp;[P0428R2 zwykłego składni szablonu dla ogólnego wyrażeń lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Nie|
|&nbsp;&nbsp;[Domyślna P0683R1 inicjatorów elementów członkowskich dla pól bitowych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html)|Nie|
|&nbsp;&nbsp;[Ustalania P0704R1 const l-wartością kwalifikowana ref wskaźników do elementów członkowskich](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|Nie|
|&nbsp;&nbsp;[Pojęcia dotyczące P0734R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf)|Nie|


## <a name="standard-library-features"></a>Funkcje standardowej biblioteki

|Obszar funkcji| |
|---|---|
|__Funkcje 20 standardowej biblioteki języka c ++__|__Obsługiwane__|
|&nbsp;&nbsp; [Unikanie niepotrzebnych zanikania P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Nie|
|&nbsp;&nbsp;[Make_shared() P0674R1 dla tablic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Nie|
|&nbsp;&nbsp;[Wymagania dotyczące iteratora Constexpr P0858R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Porównywanie P0809R0 nieuporządkowane kontenerów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp; [P0020R3 atomic\<float > niepodzielna\<podwójne > niepodzielna\<podwójnej długości >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|Nie|
|&nbsp;&nbsp; [P0053R7 \<syncstream >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br />&nbsp;&nbsp; [Osyncstream P0753R2 manipulatory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|Nie|
|&nbsp;&nbsp; [P0122R7 \<span >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|Nie|
|&nbsp;&nbsp; [P0202R3 constexpr dla \<algorytm > i exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|Nie|
|&nbsp;&nbsp; [P0355R7 \<chrono > stref czasowych i kalendarzy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|Nie|
|&nbsp;&nbsp; [P0415R1 constexpr dla \<złożonych > (ponownie)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|Nie|
|&nbsp;&nbsp; [P0439R0 wyliczenia klasy memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|Nie|
|&nbsp;&nbsp; [Starts_with()/ends_with() P0457R2 dla basic_string — / basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|Nie|
|&nbsp;&nbsp; [P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|Nie|
|&nbsp;&nbsp; [P0551R3 są jak Shalt nie Specialize szablonów funkcji std!](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0551r3.pdf)|Nie|
|&nbsp;&nbsp; [P0600R1 \[ \[nodiscard\] \] dla STL, część 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|Nie|
|&nbsp;&nbsp; [Przy użyciu P0616R0 move() w \<liczbowych >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|Nie|
|&nbsp;&nbsp; [P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|Nie|
|&nbsp;&nbsp; [P0718R2 atomic\<shared_ptr\<T >> niepodzielna\<weak_ptr\<T >>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|Nie|
|&nbsp;&nbsp; [P0754R2 \<wersji >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|Nie|
|&nbsp;&nbsp; [Wycofano P0767R1 is_pod —](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|Nie|
|&nbsp;&nbsp; [Obsługa biblioteki P0768R1 dla operatora porównania pojazdu kosmicznego \<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|Nie|
|&nbsp;&nbsp; [P0966R1 ciąg:: reserve() powinna nie zmniejszać](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0966r1.html)|Nie|
|__Funkcje 17 standardowej biblioteki języka c ++__|__Obsługiwane__|
|&nbsp;&nbsp;[Integrowanie P0433R2 wnioskowanie szablonu dla szablonów klas, do biblioteki standardowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[Poprawianie P0739R0 klasy szablonu argument wnioskowanie integracji biblioteki standardowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0426R1 constexpr dla char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[Hypot P0030R1 — (x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0220R1 biblioteki podstawy V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|2017 VS 15,6 <sup> [J](#note_J)</sup>|
|&nbsp;&nbsp;[Konwersje podstawowe ciąg P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15.7 <sup> [charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[N4562 Podstawowe informacje na temat biblioteki: \<memory_resource >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[Usuwanie P0337R0 polymorphic_allocator przypisania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|2017 VS 15,6|
|&nbsp;&nbsp;[Algorytmy równoległe P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[Zasady przetwarzania równoległego zmiana nazwy P0336R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[Algorytmy równoległe P0394R4 powinien terminate() wyjątków](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[Połączenie P0452R1 \<liczbowych > algorytmy równoległe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0226R1 specjalne funkcje matematyczne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 ścieżek względnych dla systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[Wpis katalogu P0317R1 buforowanie plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p03179r1.html)<br />&nbsp;&nbsp;[Obsługa P0392R0 string_view w ścieżki systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[Systemy plików z systemem innym niż POSIX P0430R2 obsługi](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 rozpoznawania NB komentarze dotyczące systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup> [K](#note_K)</sup>|
|&nbsp;&nbsp;[Specyfikacje wyjątków dynamicznych usuwanie P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[Poprawki P0358R1 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zmieniając P0033R1 enable_shared_from_this —](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|2017 VS 15,5 CALA <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Mapy łączenia P0083R3 i zestawów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[Wyjaśnienie P0508R0 insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Części biblioteki Vestigial wycofano P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Std::function P0302R1 usuwanie alokatora do obsługi](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T [] >, shared_ptr\<T [N] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[Shared_ptr — ustalania P0497R0 dla tablic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|2017 VS 15,5 CALA <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Wycofano P0521R0 shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zmienne wbudowane P0607R0 dla biblioteki standardowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Wycofano P0618R0 \<codecvt >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Podstawowe informacje na temat biblioteki: search() Boyer Moore](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 ustalania poszukującego zwracane typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 constexpr dla \<tablicy > (ponownie) i \<iteratora >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Narzędzia do zarządzania Rozszerzanie pamięci P0040R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 Emplace typu zwracanego](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size itp.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Zablokuj ze zmienną liczbą argumentów zmiana nazwy P0156R2\_zabezpieczenia do zakresie\_blokady](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r2.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|2017 VS 15 USTĘP 3 <sup> [L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15 ustęp 3 <sup> [17](#note_17), [bajtów](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 UDL dla \<string_view > ("meow" sv itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0418R2 atomic compare_exchange memory_order wymagania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|2017 VS 15 USTĘP 3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Common_type przeglądu P0435R1 —](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[Dostosowywanie P0548R1 typowe\_typ i czas trwania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|2017 VS 15 USTĘP 3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 constexpr dla \<chrono > (ponownie)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0513R0 zatruwaniem wyznaczania wartości skrótu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[P0599R1 noexcept wyznaczania wartości skrótu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|2017 VS 15 USTĘP 3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Oznaczenie P0516R0 shared_future — kopiowanie jako noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|2017 VS 15 USTĘP 3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Konstruowanie P0517R0 future_error — z future_errc —](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|2017 VS 15 USTĘP 3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0558R1 rozpoznawania atomic<T> o nazwie niespójności klasy podstawowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|2017 VS 15 USTĘP 3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Zmiana P0604R0 jest\_można wywołać wyniku/\_z do wywołania\_wyniku, jest\_wywoływać, jest\_nothrow\_wywoływać](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|2017 VS 15 USTĘP 3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Podstawowe informacje na temat biblioteki: \<algorytm > sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 Podstawowe informacje na temat biblioteki: \<żadnych >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 Podstawowe informacje na temat biblioteki: \<opcjonalne >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 |
|&nbsp;&nbsp;[N4562 Podstawowe informacje na temat biblioteki: \<string_view >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 Podstawowe informacje na temat biblioteki: \<krotki > apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[P0032R3 jednorodnych interfejs dla variant/any/opcjonalnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<variant >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Integrowanie P0254R2 string_view i std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 wprowadzania opcjonalne większa równości ponownie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Tworzenie P0393R3 Variant większa równości](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[Ponowne odwiedzanie P0504R0 in_place_t/in_place_type_t\<T > / in_place_index_t\<I >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[Warianty odrzucając P0510R0 z nic, tablice odwołań i niekompletne typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[Poprawa N4387 pary i spójnej kolekcji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Shared_mutex N4508 (Untimed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Usuwanie P0004R1 przestarzałe aliasów iostream](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup> [rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 zmiennej szablonów dla cech typu w kompilatorze (is_same_v itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 logiczny Operator cech typu w kompilatorze (łącznie itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Owner_less — P0074R0\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<chrono > floor(), ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Lock_guard P0156R0 ze zmienną liczbą argumentów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Unique_ptr N4089 bezpieczne konwersje w\<T [] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 usuwanie operatorów auto_ptr, random_shuffle() i starych \<funkcjonalności > rzeczy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup> [rem](#note_rem)</sup>|
|&nbsp;&nbsp;[Noexcept N4258 czyszczenia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Reference_wrapper — N4277 Trivially Copyable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Insert_or_assign()/try_emplace() N4279 dla mapy/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size(), empty(), przyczyny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Unique_ptr N4366 dokładnie ograniczający przypisania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Standardowa biblioteka C11 P0063R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 Obsługa niekompletne typy w wektor/listy/forward_list —](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|__Funkcji c ++ 14 biblioteki standardowej__|__Obsługiwane__|
|&nbsp;&nbsp;[Result_of — przyjaznego techniki SFINAE N3462](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr dla \<złożonych >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr dla \<chrono >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr dla \<tablicy >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr dla \<initializer_list >, \<krotki >, \<narzędzie >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 UDL dla \<chrono >, \<ciągu > (1729ms, "meow" s itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Wartości Null do przodu Iteratory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Heterogenicznych asocjacyjnej wyszukiwania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[Integer_sequence — N3658](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[Shared_mutex N3659 (czasem)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[Ustalania N3669 constexpr element członkowski funkcji bez const](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T >)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 Podwójny Range equal(), is_permutation(), mismatch()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Cofania alokacji o rozmiarze](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 UDL dla \<złożonych > (3.14i, itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr dla \<funkcjonalności >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[Zmiana nazwy N3891 shared_mutex (czasem) do shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 Wymagania dotyczące elementu kontenera minimalnego](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[Przezroczysty Funktorów Operator N3421 (mniej\<> itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 Alias szablonów dla \<type_traits > (decay_t, itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 Ograniczanie rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|Brak|

Grupy razem na liście dokumentów wskazuje, że funkcja została Głosowany do standardowego i następnie jeden lub więcej dokumentów do poprawy lub rozwiń tej funkcji również zostały odrzucone. Te funkcje są implementowane razem.

### <a name="supported-values"></a>Obsługiwane wartości

__Nie__ oznacza, że nie została jeszcze zaimplementowana.  
__Częściowe__ oznacza do implementacji w Visual Studio 2017 jest niekompletna. Aby uzyskać więcej informacji zobacz sekcję Uwagi.  
__N/d__ oznacza, że dokumenty propozycji opisano funkcje. Te dokumenty zmienić język standardowe, ale nie utworzono żadnej pracy dla obiektów implementujących. Są one wyświetlane tutaj aby informacje były kompletne.  
__VS 2010__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2010.  
__VS 2013__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2013.  
__VS 2015__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2015 RTM.  
__VS 2015.2__ i __VS 2015.3__ wskazać funkcje, które są obsługiwane w programie Visual Studio 2015 Update 2 i Visual Studio 2015 Update 3, odpowiednio.  
__VS 2017__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 RTM.  
__VS 2017 15 ustęp 3__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 wersji 15 ustęp 3.  
__15,5 cala 2017 VS__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 wersji 15,5 cala.
__VS 2017 15.7__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 wersji 15.7.

### <a name="notes"></a>Uwagi

<a name="note_A"></a>__A__ w /std:c ++ 14 tryb specyfikacje wyjątków dynamicznych pozostają niezaimplementowana i throw() nadal jest traktowane jako synonimem \_ \_declspec(nothrow). W języku C ++ 17, specyfikacje wyjątków dynamicznych przede wszystkim zostały usunięte przez P0003R5, pozostawiając jeden vestige: throw() jest przestarzała i wymagane będzie działać jako synonimem noexcept. W /std:c ++ 17 tryb MSVC teraz odpowiada standardowego, zapewniając throw() zachowania noexcept, tj. wymuszania za pośrednictwem rozwiązania.
Opcja kompilatora /Zc:noexceptTypes-żądań naszych poprzednie działanie \_ \_declspec(nothrow). Istnieje prawdopodobieństwo, że throw() zostaną usunięte w języku C ++ 20. Ułatwiające migracji w obszarze dodano kod w odpowiedzi na te zmiany w standardowej i naszych implementacji nowego ostrzeżenia kompilatora problemów specyfikacji wyjątku **/std:c ++ 17** i **/permissive-**.  
<a name="note_B"></a>__B__ obsługiwane w /permissive-mode w Visual Studio 2017 wersji 15.7. Zobacz [Obsługa wyszukiwania nazw dwufazowego zawiera MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/) Aby uzyskać więcej informacji.  
<a name="note_C"></a>__C__ kompilatora obsługi techniki SFINAE wyrażeń został wystarczające do biblioteki standardowej od programu Visual Studio 2015 Update 2. Obsługiwane w programie Visual Studio 2017 15.7 niezależnie od tego, czy ustawiono /permissive-mode. Niektóre usterki, nadal można naprawić. "Unikatowy tag typu" obejście nie jest już konieczne, a usunęliśmy to rozwiązanie z naszych wdrożenie STL.  
<a name="note_D"></a>__D__ obsługa kompilatora preprocesora C99 reguły jest niekompletne w Visual Studio 2017 r. Makra Wariadyczne są obsługiwane, ale istnieje wiele usterek w zachowaniu preprocesora.  Firma Microsoft są przeglądu preprocesora i doświadczalnie udostępni te zmiany w obszarze **/ ograniczająca-** tryb wkrótce.  
<a name="note_E"></a>__E__ to jest oznaczona jako nie dotyczy, ponieważ kompilatory są dozwolone, ale nie wymagane do obsługi typów rozszerzoną liczby całkowitej.  Podobnie jak GCC i Clang możemy zawarto nie do ich obsługi.  
<a name="note_F"></a>__F__ podobnie, jest to oznaczona jako nie dotyczy, ponieważ kompilatory są dozwolone, ale nie jest to wymagane, aby zaimplementować tego rodzaju optymalizacji.  
<a name="note_G"></a>__G__ obsługiwany w ramach [/std:c ++ 14](./build/reference/std-specify-language-standard-version.md) suppressible ostrzeżenia.  
<a name="note_J"></a>__J__ funkcje, które nie zostały ukończone w programie Visual Studio 2015 są podzielone w innym miejscu w tej tabeli.  
<a name="note_K"></a>__K__ to całkowicie nowe implementacji niezgodne z poprzednią wersją std::experimental wymuszone przez obsługę łącza symbolicznego, poprawki błędów i zmiany w zachowaniu wymagane standard. Obecnie w tym \<filesystem > udostępnia nowe std::filesystem i poprzednich std::experimental::filesystem i, w tym \<eksperymentalne/systemu plików > udostępnia starego eksperymentalne implementację. Eksperymentalne wdrożenia zostaną usunięte w następnej wersji podziału ABI bibliotek.  
<a name="note_L"></a>__L__ obsługiwany przez wewnętrznych kompilatora.   
<a name="note_14"></a>__14__ C ++ 17/20 funkcje te są zawsze włączone, nawet wtedy, gdy [/std:c ++ 14](build/reference/std-specify-language-standard-version.md) określono (ustawienie domyślne). To być spowodowane funkcję został wdrożony przed wprowadzeniem **/std** opcje lub powodu niepożądanie złożonych warunkowego implementacji.  
<a name="note_17"></a>__17__ te funkcje są włączone przez [/std:c ++ 17](./build/reference/std-specify-language-standard-version.md) (lub [/std:c ++ najnowsze](./build/reference/std-specify-language-standard-version.md)) — opcja kompilatora.  
<a name="note_byte"></a>__Bajt__ `std::byte` jest włączana przez [/std:c ++ 17](./build/reference/std-specify-language-standard-version.md) (lub [/std:c ++ najnowsze](./build/reference/std-specify-language-standard-version.md)), ale ponieważ może ona konflikt z nagłówkami zestaw Windows SDK w niektórych przypadkach, ma szczegółowych makro zrezygnować. Można ją wyłączyć, definiując `_HAS_STD_BYTE` jako `0`.  
<a name="note_C11"></a>__C11__ uniwersalne środowisko CRT zaimplementowana części biblioteki standardowej C11, które są wymagane przez C ++ 17, z wyjątkiem C99 `strftime()` E/O alternatywnych konwersji Specyfikatory, C11 `fopen()` trybu wyłączności i C11 `aligned_alloc()`. Jest prawdopodobnie nie będzie zaimplementowana, ponieważ określona C11 `aligned_alloc()` w taki sposób, który nie jest zgodna z implementacją Microsoft `free()`, to znaczy, że `free()` musi mieć możliwość obsługi dużej wyrównany alokacji.  
<a name="note_rem"></a>__rem__ funkcje usunięte podczas [/std:c ++ 17](./build/reference/std-specify-language-standard-version.md) (lub [/std:c ++ najnowsze](./build/reference/std-specify-language-standard-version.md)) określono opcję kompilatora. Te funkcje zostały makra Wypisz: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`, i `_HAS_UNEXPECTED`.  
<a name="note_charconv"></a>__charconv__ from_chars() i to_chars() są dostępne dla liczb całkowitych. Obecnie pracujemy nad from_chars() liczb zmiennoprzecinkowych, przestrzegać to_chars() zmiennoprzecinkowych.  
<a name ="note_parallel"></a> __równoległe__ C ++ 17 dla biblioteki algorytmów równoległych została ukończona. Należy pamiętać, że to nie oznacza każdy algorytm jest zarządzana z przetwarzaniem w każdym przypadku. zarządzana przetwarzaniem najważniejszych algorytmów i podpisy zasad wykonywania są udostępniane, nawet gdy algorytmy są nie została zrównoleglona. Nagłówka centralnego wewnętrzny implementacja naszej STL, yvals.h, zawiera następujące "Parallel algorytmów uwagi": C++ pozwala implementację do zaimplementowania algorytmy równoległe jako wywołania serial algorytmów.   Ta implementacja parallelizes kilka typowych wywołań algorytmu, ale nie wszystkich.  

Zarządzana są przetwarzaniem następujących algorytmów:

- adjacent_difference, adjacent_find —, all_of, any_of, count, count_if, równości, exclusive_scan, znajdowanie, find_end —, find_first_of, find_if, for_each, for_each_n, inclusive_scan, niezgodność, none_of, zmniejszyć, Usuń, remove_if, wyszukiwania, search_n —, sortowania, stable_ sortowanie, transformacja, transform_exclusive_scan, transform_inclusive_scan, transform_reduce.

Poniżej są nie obecnie została zrównoleglona:

- Nie jawnego równoległości zwiększenie wydajności na urządzeniu docelowym; Wszystkie algorytmy, które jedynie kopiowania lub permute — elementy z gałęzi są zazwyczaj ograniczone przepustowość pamięci:
  - kopiowania, copy_backward —, copy_n, wypełnienie, fill_n, move, move_backward, Usuń, remove_if, Zamień, replace_if, wstecznego, reverse_copy, obracanie, rotate_copy, swap_ranges —
- Pomyłek za pośrednictwem wymagania równoległości użytkownika istnieje; prawdopodobnie w powyższych kategorii mimo to:
  - Generowanie generate_n
- Równoległość skuteczne podejrzenie, że było:
  - partial_sort, partial_sort_copy
- Nie został jeszcze sprawdzony; Równoległość może być wdrażana w przyszłej wersji i może być korzystne:
  - copy_if, obejmuje, inplace_merge —, is_heap, is_heap_until —, is_partitioned, is_sorted, is_sorted_until —, lexicographical_compare —, max_element, scalania, min_element, minmax_element, nth_element, partition_copy —, remove_copy, remove_copy_if, replace_ kopiowanie, replace_copy_if, set_difference —, set_intersection —, set_symmetric_difference —, set_union —, stable_partition —, unikatowe, unique_copy —

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](cpp/cpp-language-reference.md)  
[Standardowa biblioteka C++](standard-library/cpp-standard-library-reference.md)  
[Ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md)  
[Co nowego w języku Visual C++ w programie Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md)  
[Visual C++ historii zmian 2003 za pośrednictwem 2015](porting/visual-cpp-change-history-2003-2015.md)  
[Visual C++ — co nowego od roku 2003 do 2015](porting/visual-cpp-what-s-new-2003-through-2015.md)  
[Blogu zespołu Visual C++](https://blogs.msdn.microsoft.com/vcblog/)  
