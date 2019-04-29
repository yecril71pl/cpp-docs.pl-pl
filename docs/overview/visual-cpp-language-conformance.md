---
title: Zgodność języka Visual C++
ms.date: 11/15/2017
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 69591186550a915edb49889617740e454817f154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351959"
---
# <a name="visual-c-language-conformance"></a>Zgodność języka Visual C++

Ten temat zawiera podsumowanie ISO C ++ 03, C ++ 11, C ++ 14, C ++ 17 i projekt C ++ 20 języka zgodność ze standardami funkcje kompilatora i biblioteki standardowej funkcji dla kompilatora języka C++ w Visual Studio 2017 i wcześniejszych wersji. Każdy kompilator i biblioteki standardowej funkcji Nazwa łącza do standardu ISO C++ papieru wniosek, który zawiera opis funkcji, jeśli jest dostępny w momencie publikacji. Kolumna obsługiwane zawiera listę wersji programu Visual Studio, w której obsługa dla funkcji najpierw pojawiły się.

Aby uzyskać więcej informacji na temat udoskonaleń zgodności i inne zmiany w programie Visual Studio 2017, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements.md) i [What's New for Visual C++ w programie Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md). Zgodność ze zmian we wcześniejszych wersjach, zobacz [Visual C++ — Historia zmian](../porting/visual-cpp-change-history-2003-2015.md) i [Visual C++ co w nowym roku 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Aby uzyskać bieżące informacje od zespołu języka C++, odwiedź stronę [blog zespołu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

> [!NOTE]
> Nie ma żadnych danych binarnych przełomowych zmian między wersjami programu Visual Studio 2015 i Visual Studio 2017.

## <a name="compiler-features"></a>Funkcje kompilatora

|Obszar funkcji| |
|----|---|
|__C ++ 03/11 podstawowe funkcje językowe__|__Obsługiwane__|
|&nbsp;&nbsp;Wszystkie inne elementy|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;Dwufazowe wyszukiwanie nazw|PREMIERA PROGRAMU VS 2017 WERSJI 15.7 <sup> [B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 Expression SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[N1653 procesor C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Częściowe <sup> [D](#note_D)</sup>|
|&nbsp;&nbsp;[Rozszerzony N1988 typów całkowitych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|N/D <sup> [E](#note_E)</sup>|
|__C ++ 14 podstawowe funkcje językowe__|__Obsługiwane__|
|&nbsp;&nbsp;[Konwersje kontekstowe N3323 Tweaked sformułowanie funkcji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[Literały binarne N3472](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[Automatycznie N3638 i decltype(auto) typy zwracane](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init przechwytywania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 ogólnych wyrażeń lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[Atrybut N3760 [[deprecated]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[Rozmiar N3778 cofania alokacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[Separatory cyfr N3781](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[Szablony N3651 zmiennej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[Rozszerzony N3652 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[NSDMIs N3653 dla wartości zagregowanych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 Alokacje elementem zespalając zapobieganie /](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|N/D <sup> [F](#note_F)</sup>|
|__C ++ 17 podstawowe funkcje językowe__|__Obsługiwane__|
|&nbsp;&nbsp;[Usuwanie N4086 trójznaków](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 nowe reguły automatycznej z kopiowaniem list inicjacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Typename N4051 za parametrów szablonu szablonu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Atrybuty N4266 dla przestrzeni nazw oraz wyliczeń](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Literały znakowe u8 N4267](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Zagnieżdżone N4230 definicji przestrzeni nazw](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Zwięzła N3928 static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Uogólnione P0184R0 opartej na zakresie pętle](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 atrybut [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 usuwanie register — słowo kluczowe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Usuwanie P0002R1 operator ++ dla bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Przechwytywanie P0018R3 * to według wartości](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 przy użyciu atrybutu przestrzeni nazw bez powtarzania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 bezpośrednio list inicjowania typów stałych wyliczeniowych z liczb całkowitych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Lambdy wyrażeń constexpr P0170R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 atrybut [[nodiscard]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 atrybut [[maybe_unused]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Powiązania strukturalne P0217R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Instrukcji if P0292R2 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [G](#note_G)</sup>|
|&nbsp;&nbsp;[Instrukcje wyboru P0305R1 z inicjatorami](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Literałów typu Hexfloat P0245R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Co N4268 więcej argumentów szablonu bez typu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 złożyć wyrażenia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Usuwanie P0003R5 dynamiczne wyjątek specyfikacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Dodawanie P0012R1 noexcept do systemu typów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 nadmiernie wyrównanych dynamicznej alokacji pamięci](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zmienne śródwierszowe P0386R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Dopasowywanie P0522R0 szablonu — parametry szablonu zgodne argumentów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Usuwanie P0036R0 niektóre pusty złożeń jednoargumentowy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Naprawianie N4261 konwersji kwalifikacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|PREMIERA PROGRAMU VS 2017 WERSJI 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Rozszerzony P0017R1 inicjowania agregacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|PREMIERA PROGRAMU VS 2017 WERSJI 15.7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Wnioskowanie argumentu szablonu P0091R3 dla szablonów klas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[Problemy Wnioskowanie argumentu szablonu klasy P0512R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Deklarowanie P0127R2 parametry szablonu bez typu, dzięki funkcji autoskalowania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Gwarantowana P0135R1 pominięcia kopii](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6|
|&nbsp;&nbsp;[Zmiana sformułowania elementu P0136R1, konstruktory dziedziczące](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Rafinacja P0145R3 kolejność obliczania wyrażeń](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 kolejność obliczania argumenty funkcji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Rozwinięcia P0195R2 Pack w deklaracjach using](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 ignoruje nieznane atrybuty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|

|Obszar funkcji| |
|----|---|
|__C ++ 17 podstawowych funkcji języka (zgłoszeń wad)__|__Obsługiwane__|
|&nbsp;&nbsp;[Naprawianie P0702R1 klasy odliczanie argumentu szablon na liście inicjatora konstruktory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Upraszczanie P0588R1 przechwytywania lambda niejawne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|Nie|
|&nbsp;&nbsp;[CWG 1581: Gdy są zdefiniowane funkcje Członkowskie constexpr](https://wg21.cmeerw.net/cwg/issue1581)|Nie|
|&nbsp;&nbsp;[P0962R1 złagodzić Dostosowywanie powiązań strukturalnych punktu reguły wyszukiwania](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|Nie|
|&nbsp;&nbsp;[P0962R2 złagodzić zakres — punkt dostosowywania pętli znajdowanie reguły](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|Nie|
|&nbsp;&nbsp;[P0969R0, dzięki czemu mają strukturę powiązania z dostępne elementy członkowskie](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|Nie|

|Obszar funkcji| |
|----|---|
|__20 podstawowe funkcje języka c ++__|__Obsługiwane__|
|&nbsp;&nbsp;[Dodawanie P0306R4 &#95; &#95;VA_OPT&#95; &#95; pominięcie przecinek i usuwania przecinkami](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0306r4.html)|Nie|
|&nbsp;&nbsp;[Wyznaczony P0329R4 inicjowania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|Nie|
|&nbsp;&nbsp;[Co P0409R2 lambda-capture [=, to]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|Nie|
|&nbsp;&nbsp;[P0428R2 znanej składni szablonu dla ogólnych wyrażeń lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Nie|
|&nbsp;&nbsp;[Domyślne P0683R1 inicjatorów składowych dla pól bitowych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html)|Nie|
|&nbsp;&nbsp;[Naprawianie P0704R1 const l-wartości kwalifikowana ref wskaźników do elementów członkowskich](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|Nie|
|&nbsp;&nbsp;[Pojęcia dotyczące P0734R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf)|Nie|

## <a name="standard-library-features"></a>Funkcje biblioteki standardowej

|Obszar funkcji| |
|---|---|
|__Funkcje 20 standardowej biblioteki c ++__|__Obsługiwane__|
|&nbsp;&nbsp; [Unikanie niepotrzebnych zanikania P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Nie|
|&nbsp;&nbsp;[Make_shared() P0674R1 dla tablic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Nie|
|&nbsp;&nbsp;[Wymagania dotyczące iteratora Constexpr P0858R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0809R0 porównanie, nieuporządkowane kontenery](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp; [P0020R3 atomic\<float > niepodzielna\<double > niepodzielna\<typu long double >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|Nie|
|&nbsp;&nbsp; [P0053R7 \<syncstream>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br />&nbsp;&nbsp; [Osyncstream P0753R2 manipulatory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|Nie|
|&nbsp;&nbsp; [P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|Nie|
|&nbsp;&nbsp; [P0202R3 constexpr dla \<algorytm > i funkcja exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|Nie|
|&nbsp;&nbsp; [P0355R7 \<chrono > stref czasowych i kalendarze](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|Nie|
|&nbsp;&nbsp; [P0415R1 constexpr dla \<złożonych > (ponownie)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|Nie|
|&nbsp;&nbsp; [Memory_order klasy enum P0439R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|Nie|
|&nbsp;&nbsp; [Starts_with()/ends_with() P0457R2 dla basic_string/basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|Nie|
|&nbsp;&nbsp; [P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|Nie|
|&nbsp;&nbsp; [P0551R3 są jak Shalt nie specjalizują się standardowe szablony funkcji!](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0551r3.pdf)|Nie|
|&nbsp;&nbsp; [P0600R1 \[ \[nodiscard\] \] dla STL, część 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|Nie|
|&nbsp;&nbsp; [Za pomocą P0616R0 move() w \<liczbowych >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|Nie|
|&nbsp;&nbsp; [P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|Nie|
|&nbsp;&nbsp; [P0718R2 atomic\<shared_ptr\<T >> niepodzielna\<weak_ptr\<T >>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|Nie|
|&nbsp;&nbsp; [P0754R2 \<wersja >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|Nie|
|&nbsp;&nbsp; [Is_pod P0767R1 wycofano](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|Nie|
|&nbsp;&nbsp; [Operator porównania pojazdu kosmicznego obsługę biblioteki P0768R1 \<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|Nie|
|&nbsp;&nbsp; [P0966R1 ciągu:: reserve() nie powinno zmniejszyć.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0966r1.html)|Nie|
|__Funkcji c ++ 17 biblioteki standardowej__|__Obsługiwane__|
|&nbsp;&nbsp;[Integrowanie P0433R2 wnioskowanie szablonu dla szablonów klas, do biblioteki standardowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[Poprawa P0739R0 klasy argument wnioskowanie integracji szablonu do biblioteki standardowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0426R1 constexpr dla char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[Hypot P0030R1 — (x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[Podstawowe informacje dotyczące biblioteki P0220R1 w wersji 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|PREMIERA PROGRAMU VS 2017 15.6 <sup> ["J"](#note_J)</sup>|
|&nbsp;&nbsp;[P0067R5 podstawowe ciąg konwersje](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|Program VS 2017 w wersji 15.7 <sup> [charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[N4562 Dokumentu Library Fundamentals: \<memory_resource >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[Usuwanie P0337R0 polymorphic_allocator przypisania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[Algorytmy równoległe P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[Zasady wykonywania równoległego zmiana nazwy P0336R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[Algorytmy równoległe P0394R4 powinien terminate() dla wyjątków](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[P0452R1, ujednolicając naukę \<liczbowych > algorytmy równoległe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0226R1 specjalne funkcje matematyczne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 ścieżki względne do plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[Wpis katalogu P0317R1 buforowania dla systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br />&nbsp;&nbsp;[Obsługa P0392R0 string_view w ścieżkach systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[Systemy plików POSIX bez obsługi P0430R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 rozpoznawanie NB komentarzy do systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup>[K](#note_K)</sup>|
|&nbsp;&nbsp;[Specyfikacje wyjątków dynamicznych usuwanie P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 poprawek not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zmiana sformułowania elementu P0033R1 enable_shared_from_this —](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|PREMIERA PROGRAMU VS 2017 15.5 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0083R3 łączenie map i zestawów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[Wyjaśnienie P0508R0 insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 wycofano przestarzały biblioteki części](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Std::function P0302R1 usuwanie alokatora do obsługi](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T [] >, shared_ptr\<T [N] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[Naprawianie P0497R0 shared_ptr dla tablic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|PREMIERA PROGRAMU VS 2017 15.5 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Wycofano P0521R0 shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 zmienne śródwierszowe standardowej biblioteki](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Wycofano P0618R0 \<codecvt >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Dokumentu Library Fundamentals: Boyer-Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 ustalania wykryć typy zwracane](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 constexpr dla \<array > (ponownie) i \<iterator >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Narzędzia do zarządzania Rozszerzanie pamięci P0040R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 emplace — typ zwracany](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size itp.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Zablokuj P0156R2 zmiana nazwy zmiennych\_je przed nieprzewidzianymi do zakresu\_blokady](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|Program VS 2017 15.3 <sup> [17](#note_17), [bajtów](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 UDL dla \<string_view > ("meow" sv itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0418R2 atomic compare_exchange memory_order wymagania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Common_type P0435R1 przeglądu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[Dostosowywanie P0548R1 typowe\_typ i czas trwania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 constexpr dla \<chrono > (ponownie)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Skażające P0513R0 wyznaczania wartości skrótu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[Operator noexcept P0599R1 wyznaczania wartości skrótu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Oznaczanie P0516R0 shared_future — kopiowanie jako noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Konstruowanie P0517R0 future_error z future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0558R1 rozpoznawanie atomic<T> o nazwie niespójności klasy podstawowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Zmiana P0604R0 jest\_wywoływalnej/wyników\_elementu do wywołania\_wyniku, jest\_można wywołać, jest\_nothrow\_można wywołać](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|PREMIERA PROGRAMU VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Dokumentu Library Fundamentals: \<algorytm > sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 Dokumentu Library Fundamentals: \<wszelkie >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 Dokumentu Library Fundamentals: \<opcjonalne >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 |
|&nbsp;&nbsp;[N4562 Dokumentu Library Fundamentals: \<string_view >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 Dokumentu Library Fundamentals: \<krotki > apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[P0032R3 jednorodny interfejs dla wariantu/any/opcjonalne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<wariantu >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Integrowanie P0254R2 string_view i std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 podejmowanie opcjonalna większa równe ponownie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Podejmowanie P0393R3 Variant większa równości](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[Ponowne spojrzenie na P0504R0 in_place_t/in_place_type_t\<T > / in_place_index_t\<mogę >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[Odrzuca P0510R0 wariantów z Nothing, tablice, odwołania i niekompletnych typów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[Poprawa N4387 parę i krotki](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Shared_mutex N4508 (Untimed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Usuwanie P0004R1 przestarzałe aliasów iostream](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup> [rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 zmienne szablony dla cech typu (is_same_v itp.).](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 logiczne cech typu operatora (połączeniu itp.).](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Owner_less — P0074R0\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<chrono > floor() ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Lock_guard P0156R0 ze zmienną liczbą argumentów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Unique_ptr N4089 bezpiecznej konwersji w\<T [] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Usuwanie N4190 auto_ptr, random_shuffle() i starych \<funkcjonalności > rzeczy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[Operator noexcept N4258 przesłali](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Reference_wrapper N4277 Trywialne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() For map/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size(), empty(), data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Unique_ptr N4366 dokładnie ograniczając przypisania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Standardowa biblioteka C11 P0063R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 obsługi niekompletne typy w wektor/list/forward_list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|__Funkcji c ++ 14 biblioteki standardowej__|__Obsługiwane__|
|&nbsp;&nbsp;[Result_of — przyjaznego SFINAE N3462](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr dla \<złożonych >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr dla \<chrono >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr dla \<tablicy >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr dla \<initializer_list >, \<krotki >, \<Narzędzia >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 UDL dla \<chrono >, \<ciągu > (1729ms, "meow" s itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Tworzyć Iteratory do przodu o wartości Null](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[Funkcja quoted() N3654](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Heterogeniczne wyszukiwanie asocjacyjne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[Shared_mutex N3659 (czasem)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[Naprawianie N3669 constexpr element członkowski funkcji bez const](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[Pobierz N3670\<T >)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 Funkcje Dwuzakresowymi, podwójnym zakresie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Dezalokacji wielkości](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 UDL dla \<złożonych > (ciąg 3.14i, itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr dla \<funkcjonalności >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 alias typu tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[Zmiana nazwy N3891 shared_mutex (czasem) do shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 Wymagania dotyczące elementu kontenera minimalny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 przezroczyste Funktory operatora (mniej\<> itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 Alias szablonów dla \<type_traits > (decay_t, itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 Ograniczanie rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|Brak|

Grupa dokumentów razem na liście wskazuje, że funkcja została wybrana w standardowej, a następnie co najmniej jeden dokumentów, aby zwiększyć lub rozszerzyć tę funkcję również pod głosowanie. Te funkcje są wdrażane razem.

### <a name="supported-values"></a>Obsługiwane wartości

__Nie__ oznacza, że nie została jeszcze zaimplementowana.<br/>
__Częściowe__ oznacza, że wdrożenia w programie Visual Studio 2017 nie została ukończona. Aby uzyskać więcej informacji zobacz sekcję Uwagi.<br/>
__N/d__ oznacza, że dokumentacja propozycji nie opisano funkcje. Te dokumenty zmieniony język standardowych, ale nie utworzono wszelkie prace dotyczące implementacji. Są one wyświetlane tutaj aby informacje były kompletne.<br/>
__VS 2010__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2010.<br/>
__VS 2013__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2013.<br/>
__Program VS 2015__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2015 RTM.<br/>
__VS 2015.2__ i __VS 2015.3__ wskazać funkcje, które są obsługiwane w programie Visual Studio 2015 Update 2 i programu Visual Studio 2015 Update 3, odpowiednio.<br/>
__Premiera programu VS 2017__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 RTM.<br/>
__Program VS 2017 15.3__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15.3.<br/>
__Program VS 2017 15.5__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15.5.<br/>
__Program VS 2017 w wersji 15.7__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 wersji 15.7.<br/>

### <a name="notes"></a>Uwagi

<a name="note_A"></a>__A__ w/STD: c ++ 14 tryb specyfikacje wyjątków dynamicznych pozostają niezaimplementowana i throw() nadal jest traktowany jako synonim dla \_ \_declspec(nothrow). W języku C ++ 17, specyfikacje wyjątków dynamicznych zostały usunięte przede wszystkim przez P0003R5, pozostawiając jeden vestige: throw() jest przestarzała i trzeba zachowywać się jak synonimem noexcept. W/STD: c ++ 17 tryb MSVC jest teraz zgodny ze standardem, zapewniając throw() takie samo zachowanie jako noexcept, czyli wymuszania za pośrednictwem rozwiązania.

Opcja kompilatora /Zc:noexceptTypes-żądań nasze poprzednie działanie \_ \_declspec(nothrow). Istnieje prawdopodobieństwo, że throw() zostaną usunięte w języku C ++ 20. Pomagające w migracji dodano kod w odpowiedzi na te zmiany w wersji Standard i naszej implementacji nowe ostrzeżenia kompilatora problemów specyfikacji wyjątku w ramach **/STD: c ++ 17** i **/permissive-**.

<a name="note_B"></a>__B__ obsługiwane w /permissive-mode w programie Visual Studio 2017 wersji 15.7. Zobacz [nazwa dwufazowe wyszukiwanie obsługuje już MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/) Aby uzyskać więcej informacji.

<a name="note_C"></a>__C__ kompilatora obsługę wyrażenie SFINAE został wystarczające do biblioteki standardowej od programu Visual Studio 2015 Update 2. Obsługiwane w programie Visual Studio 2017 w wersji 15.7, niezależnie od tego, czy ustawiono /permissive-mode. Niektóre błędy pozostają naprawy. Rozwiązanie "unikatowych tagów type" nie jest już konieczne i usunęliśmy to obejście z naszej implementacji STL.

<a name="note_D"></a>__D__ obsługa kompilatora do reguły Preprocesor C99 została ukończona w programie Visual Studio 2017. Makra Wariadyczne są obsługiwane, ale istnieje wiele błędów w działaniu preprocesora.  Firma Microsoft jest przeglądu preprocesora i doświadczalnie udostępni te zmiany w obszarze **/ permissive-** tryb wkrótce.

<a name="note_E"></a>__E__ to jest oznaczona jako nie ma zastosowania, ponieważ kompilatory są dozwolone, ale nie jest to wymagane, aby obsługiwać rozszerzone typy liczb całkowitych.  Podobnie jak GCC i Clang Wybraliśmy nie do ich obsługi.

<a name="note_F"></a>__F__ podobnie, jest on oznaczony jako nie ma zastosowania, ponieważ kompilatory są dozwolone, ale nie jest to wymagane, aby zaimplementować tego rodzaju optymalizacji.

<a name="note_G"></a>__G__ objęte [/STD: c ++ 14](../build/reference/std-specify-language-standard-version.md) suppressible ostrzeżenie.

<a name="note_J"></a>__"J"__ funkcje, które nie zostały ukończone w programie Visual Studio 2015 są rozbite innych miejscach w tej tabeli.

<a name="note_K"></a>__K__ jest całkowicie nową metodę implementacji, niezgodna z poprzednią wersją std::experimental wymuszone przez Link symboliczny dział pomocy technicznej, poprawki błędów i zmiany w zachowaniu wymagane przez standard. Obecnie, w tym \<systemu plików > udostępnia std::filesystem nowej i poprzedniej std::experimental::filesystem z uwzględnieniem \<eksperymentalne/systemu plików > udostępnia stare eksperymentalne implementację. Eksperymentalne implementację zostanie USUNIĘTY w następnej wersji interfejsu ABI podziału bibliotek.

<a name="note_L"></a>__L__ obsługiwane przez wewnętrzne polecenie kompilatora.

<a name="note_14"></a>__14__ C ++ 17/20 funkcje te są zawsze włączone, nawet wtedy, gdy [/STD: c ++ 14](../build/reference/std-specify-language-standard-version.md) określono (ustawienie domyślne). Może to być, ponieważ ta funkcja została zaimplementowana przed wprowadzeniem **/STD** opcje, lub ponieważ warunkowego implementacji niepożądanych złożone.

<a name="note_17"></a>__17__ te funkcje są włączone przez [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md)) opcję kompilatora.

<a name="note_byte"></a>__bajtów__ `std::byte` został włączony przez [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md)), ale ponieważ mogą powodować konflikt z nagłówkami zestawu Windows SDK, w niektórych przypadkach, szczegółowych makro zrezygnować. Można je wyłączyć, definiując `_HAS_STD_BYTE` jako `0`.

<a name="note_C11"></a>__C11__ Universal CRT zaimplementowane części C11 biblioteki standardowej, które są wymagane przez C ++ 17, z wyjątkiem C99 `strftime()` E/O alternatywnych konwersji specyfikatory C11 `fopen()` trybie wyłączności i C11 `aligned_alloc()`. Jest prawdopodobnie nie będzie zaimplementowana, ponieważ określona C11 `aligned_alloc()` w sposób, który jest niezgodny z implementacją firmy Microsoft `free()`, to znaczy, że `free()` musi być w stanie obsłużyć bardzo wyrównany alokacji.

<a name="note_rem"></a>__rem__ funkcje usunięte, gdy [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md)) określono opcję kompilatora. Te funkcje mają makra zrezygnować: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`, i `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ from_chars() i to_chars() są dostępne dla liczb całkowitych. Obecnie pracujemy nad from_chars() zmiennoprzecinkowych, przestrzegać to_chars() zmiennoprzecinkowych.

<a name ="note_parallel"></a> __równoległe__ biblioteki algorytmów równoległych C ++ 17 firmy zostało zakończone. Należy pamiętać, że nie oznacza to, że każdy algorytm jest zrównoleglona w każdym przypadku. Najważniejsze algorytmy została zrównoleglona. i podpisy zasad wykonywania są dostarczane, nawet gdy algorytmy są nie została zrównoleglona. Nagłówek centralny wewnętrznego naszej implementacji STL, yvals.h, zawiera następujące "równoległych algorytmów uwagi dotyczące": Język C++ pozwala na implementację do zaimplementowania algorytmy równoległe jako wywołania serial algorytmów.   Ta implementacja parallelizes kilka typowych wywołań algorytmu, ale nie wszystkich.

Następujące algorytmy są zrównoleglona:

- adjacent_difference, adjacent_find, all_of, any_of, count, count_if —, równe, exclusive_scan, znajdowanie, find_end —, find_first_of —, find_if, for_each, for_each_n, inclusive_scan, niezgodność, none_of, zmniejszyć, Usuń, remove_if —, wyszukiwanie, search_n —, sortowania, stable_ sortowanie, Przekształć transform_exclusive_scan, transform_inclusive_scan, transform_reduce.

Poniżej są obecnie niezrównoleglone:

- Nie poprawę wydajności jawnego równoległości na urządzeniu docelowym; Wszystkie algorytmy, które jedynie kopiowania lub permute — elementy z gałęzi są zazwyczaj ograniczone przepustowość pamięci:
  - copy, copy_backward, copy_n, fill, fill_n, move, move_backward, remove, remove_if, replace, replace_if, reverse, reverse_copy, rotate, rotate_copy, swap_ranges
- Istnieje pomyłek za pośrednictwem wymagań równoległości użytkowników; prawdopodobnie w powyższych kategorii mimo to:
  - Generowanie generate_n
- Skuteczne równoległości podejrzewa się, że było:
  - partial_sort, partial_sort_copy
- Nie zostały jeszcze ocenione; Równoległość może być implementowana w przyszłej wersji i może być korzystne:
  - copy_if, obejmuje, inplace_merge —, is_heap, is_heap_until —, is_partitioned, is_sorted, is_sorted_until —, lexicographical_compare —, max_element, scalania, min_element, minmax_element, nth_element —, partition_copy —, remove_copy —, remove_copy_if —, replace_ Kopiuj replace_copy_if —, set_difference —, set_intersection —, set_symmetric_difference —, set_union —, stable_partition —, unikatowe, unique_copy —

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md)<br/>
[Co nowego w języku Visual C++ w programie Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historia zmian w usłudze Visual C++ 2003 do 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Visual C++ — co nowego od roku 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[Blogu zespołu Visual C++](https://blogs.msdn.microsoft.com/vcblog/)
