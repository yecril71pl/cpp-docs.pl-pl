---
title: Literał ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 41f1996cd4f4caf24ac08d09b05e636cb09f7eed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415268"
---
# <a name="string-literal"></a>Literał ciągu

Obsługa literałów ciągu zmienił się z zarządzanych rozszerzeń języka C++ do Visual C++.

W zarządzanych rozszerzeń dla projektów języka C++, literał ciągu zarządzane była wskazywana przez prefacing literał z `S`. Na przykład:

```
String *ps1 = "hello";
String *ps2 = S"goodbye";
```

Wydajność obciążenie między dwoma inicjalizacje okaże się trywialny, jako następujących CIL reprezentacji pokazuje widzianych przez **ildasm**:

```
// String *ps1 = "hello";
ldsflda    valuetype $ArrayType$0xd61117dd
     modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier)
     '?A0xbdde7aca.unnamed-global-0'

newobj instance void [mscorlib]System.String::.ctor(int8*)
stloc.0

// String *ps2 = S"goodbye";
ldstr      "goodbye"
stloc.0
```

To duże oszczędności po prostu zapamiętywanie (lub uczenia) jako prefiks literału ciągu przy użyciu `S`. W nowej składni obsługi literałów ciągów jest przezroczyste, ustalany na podstawie kontekstu użytkowania. `S` Już nie musi być określona.

Co przypadki, w których należy jawnie skierować kompilatorowi interpretacja lub innym? W takich przypadkach możemy zastosować jawnego rzutowania. Na przykład:

```
f( safe_cast<String^>("ABC") );
```

Ponadto literału ciągu jest teraz zgodny `String` za pomocą prostego konwersji, a nie standardowych konwersji. Chociaż może to brzmieć nie, takie jak znacznie zmienia rozpoznawania zestawów przeciążonej funkcji, które obejmują `String` i `const char*` jako konkurencyjnych parametrów formalnych. Rozwiązania, które po rozpoznany `const char*` wystąpienia teraz jest oznaczony jako niejednoznaczny. Na przykład:

```
ref struct R {
   void f(const char*);
   void f(String^);
};

int main () {
   R r;
   // old syntax: f( const char* );
   // new syntax: error: ambiguous
   r.f("ABC"); 
}
```

Dlaczego występuje różnica? Ponieważ więcej niż jedno wystąpienie o nazwie `f` istnieje w ramach programu, wymaga to algorytm rozpoznawania przeciążenia funkcji mają być stosowane do wywołania. Posiadanie rozpoznawanie przeciążona funkcja obejmuje trzy kroki.

1. Kolekcja funkcji Release candidate. Funkcje kandydujące są tych metod w zakresie, które leksykalnie zgodna z nazwą wywoływaną funkcję. Na przykład, ponieważ `f()` jest wywoływana za pomocą wystąpienia `R`, wszystkie nazwane funkcje `f` nie będących członkami `R` (lub jej klasa bazowa hierarchii) nie są funkcje Release candidate. W tym przykładzie istnieją dwie funkcje Release candidate. Są to dwie funkcje Członkowskie z `R` o nazwie `f`. Wywołanie nie powiedzie się w tej fazie Jeśli zestaw funkcji Release candidate jest pusty.

1. Zestaw funkcji możliwego do użycia spośród funkcji Release candidate. Funkcja możliwego do użycia to taki, który może być wywołana z argumentami określony w wywołaniu liczba argumentów i ich typy. W naszym przykładzie obu tych funkcji kandydata są również funkcje możliwego do użycia. Wywołanie nie powiedzie się w tej fazie Jeśli zestaw możliwego do użycia funkcja jest pusty.

1. Wybierz funkcję, która reprezentuje najlepsze dopasowanie wywołania. Polega to na konwersji stosowane do przekształcania argumentów na typ parametrów możliwego do użycia funkcji klasyfikacja. To jest względnie proste — przy użyciu funkcji pojedynczego parametru; staje się nieco bardziej skomplikowane, gdy istnieje wiele parametrów. Jeśli nie zostanie odnaleziony odpowiednik najlepsze, w tej fazie nie powiedzie się wywołanie. Oznacza to jeśli konieczne Przekształcenie typu rzeczywistego argumentu typu formalnego parametru konwersje są równie dobre. Wywołanie jest oznaczone jako niejednoznaczny.

W zarządzanych rozszerzeń rozwiązania dla tego wywołania wywoływane `const char*` wystąpienia jako najlepsze dopasowanie. W nowej składni konwersji dopasować `"abc"` do `const char*` i `String^` teraz są równoważne — to znaczy, równie good — i dlatego wywołanie jest oznaczony jako nieprawidłowy — oznacza to, jak niejednoznaczne.

Prowadzi to nam na dwa pytania:

- Co to jest typ rzeczywistego argumentu `"abc"`?

- Co to jest algorytm określania, gdy konwersja jednego typu jest lepsze niż innego?

Typ literału ciągu `"abc"` jest `const char[4]` — należy pamiętać, że istnieje niejawna null kończącego znaku końca każdego ciągu literału.

Algorytm określania, kiedy jeden konwersji typu jest lepsza od innego obejmuje umieszczenie konwersje typów możliwych do hierarchii. Oto mój opis tej hierarchii - takiej konwersji, oczywiście, są niejawne. Przy użyciu notacji rzutowania jawnego zastępuje hierarchii, podobnie jak nawiasy zastępuje zwykle kolejność wykonywania wyrażenia.

1. Najlepiej jest dokładne dopasowanie. Zaskakująco argumentu być dokładnym dopasowaniem, nie trzeba ją dokładnie odpowiadać typowi parametru; po prostu musi być wystarczająco blisko. Jest kluczem do zrozumienia, co się dzieje w tym przykładzie, a także jak język został zmieniony.

1. Promocja jest lepsze niż konwersja standardowa. Na przykład, podwyższanie poziomu `short int` do `int` jest lepsze niż konwertowanie `int` do `double`.

1. Konwersja standardowa jest lepsza niż konwersja boxing. Na przykład konwertowanie `int` do `double` jest lepsze pakowanie `int` do `Object`.

1. Konwersja boxing jest lepsza niż niejawna konwersja zdefiniowana przez użytkownika. Na przykład konwersja boxing `int` do `Object` jest lepsze niż zastosowanie operatora konwersji z `SmallInt` klasę wartości.

1. Niejawna konwersja zdefiniowana przez użytkownika jest lepsza niż konwersja nie jest w ogóle. Niejawna konwersja zdefiniowana przez użytkownika jest ostatni zakończenia przed błędu (z ostrzeżenie, że podpis formalny może zawierać tablica parametrów i Wielokropek na tej pozycji).

Tak co oznacza powiedzieć, że dokładne dopasowanie nie musi być dokładnie dopasowania? Na przykład `const char[4]` nie jest dokładnie dopasowana albo `const char*` lub `String^`, a jeszcze niejasności w naszym przykładzie między dwa sprzeczne dokładnymi dopasowaniami!

Dokładne dopasowanie, jak to się dzieje, obejmuje pewną liczbę trivial konwersji. Istnieją cztery proste konwersje w obszarze ISO C++ mogą być stosowane, która nadal kwalifikują się jako dokładnego dopasowania. Trzy są określane jako lvalue przekształcenia. Typ czwartego nosi nazwę konwersja kwalifikacji. Trzy przekształcenia l-wartości są traktowane jako lepiej dokładne dopasowanie niż jedno wymaganie konwersja kwalifikacji.

Jeden formularz transformacji l-wartości jest konwersja native tablicy do wskaźnika. Jest to, co jest zaangażowana w dopasowywanie `const char[4]` do `const char*`. W związku z tym, dopasowanie `f("abc")` do `f(const char*)` dokładne dopasowanie. W starszych incarnations naszych języka to w rzeczywistości była najlepsze dopasowanie.

Dla kompilatora mógł oflagować wywołania jako niejednoznaczny, dlatego wymaga konwersji `const char[4]` do `String^` również być dokładnym dopasowaniem poprzez proste konwersji. Jest to zmiana, który został wprowadzony w nowej wersji języka. I to, dlaczego wywołanie jest teraz oznaczone jako niejednoznaczny.

## <a name="see-also"></a>Zobacz też

[Ogólne zmiany w języku (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[Ciąg](../windows/string-cpp-component-extensions.md)