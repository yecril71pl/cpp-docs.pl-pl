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
ms.openlocfilehash: 9ac847f67421802fe4d31f2d66b34128e4b24794
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172411"
---
# <a name="string-literal"></a>Literał ciągu
Obsługa literałów ciągu został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W rozszerzeń zarządzanych dla projektów języka C++ literału ciągu zarządzany była wskazywana przez prefacing literał z `S`. Na przykład:  
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 Wydajność narzut między dwoma inicjalizacji okaże się nieuproszczony, jako następujące CIL reprezentacja pokazuje widziany **narzędzia ildasm**:  
  
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
  
 Jest duże oszczędności właśnie zapamiętywanie (lub uczenia) jako prefiks literału ciągu z `S`. W nowej składni Obsługa literałów ciągu jest przezroczyste, określany przez kontekst do użycia. `S` Nie będzie trzeba określić.  
  
 Jak przypadków, w których należy jawnie bezpośrednie kompilator interpretacja lub innym? W takim przypadku stosujemy jawnego rzutowania. Na przykład:  
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 Ponadto dopasowana literału ciągu `String` z prostego konwersji zamiast konwersja standardowa. Gdy to może nie dźwięk, takich jak znacznie zmienia rozpoznawania zestawów przeciążonej funkcji, które obejmują `String` i `const char*` jako konkurencyjnych parametrów formalnych. Rozwiązanie raz rozpoznać `const char*` wystąpienia teraz jest oznaczony jako niejednoznaczne. Na przykład:  
  
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
  
 Dlaczego występuje różnica? Ponieważ więcej niż jedno wystąpienie o nazwie `f` istnieje w programie, wymaga funkcji przeciążenia rozpoznawania algorytm ma zostać zastosowany do wywołania. Posiadanie Rozpoznanie przeciążenia funkcji obejmuje trzy kroki.  
  
1.  Kolekcja funkcji kandydata. Funkcje kandydujące są tych metod w zakresie, które lexically zgodna z nazwą wywoływana funkcja. Na przykład od `f()` jest wywoływany przez wystąpienie `R`, wszystkie o nazwie funkcji `f` nie są członkami `R` (lub jej klasa podstawowa hierarchii) nie są funkcje kandydujące. W naszym przykładzie istnieją dwie funkcje kandydujące. Są to funkcje Członkowskie dwóch `R` o nazwie `f`. Połączenie nie powiedzie się w tej fazie Jeśli zestaw funkcji kandydata jest pusty.  
  
2.  Zestaw funkcji działało spośród funkcji kandydata. Funkcja działało jest jedną, która może zostać wywołana z argumentami określonych w wywołaniu, liczby argumentów i ich typów. W naszym przykładzie zarówno candidate funkcje są również funkcje działało. Połączenie nie powiedzie się w tej fazie Jeśli zestaw funkcji działało jest pusty.  
  
3.  Wybierz funkcję, która reprezentuje najlepsze dopasowanie wywołania. Jest to realizowane przez Klasyfikacja konwersje stosowane do przekształcania argumenty typu parametrów funkcji działało. To jest względnie proste — przy użyciu funkcji pojedynczy parametr; staje się nieco bardziej skomplikowane, gdy istnieje wiele parametrów. Połączenie nie powiedzie się w tej fazie, jeśli nie istnieje żadne najlepsze dopasowanie. Oznacza to, że jeśli niezbędne do przekształcania typu rzeczywistego argumentu typu formalnego parametru konwersje są równie dobre. Wywołanie jest oznaczony jako niejednoznaczne.  
  
 W zarządzanych rozszerzeń rozpoznanie tego wywołania wywoływane `const char*` wystąpienia jako najlepsze dopasowanie. W nowej składni konieczne do dopasowania konwersji `"abc"` do `const char*` i `String^` teraz są równoważne — to znaczy, jednakowo good — co wywołanie jest oznaczony jako nieprawidłowy - oznacza to, jak niejednoznaczne.  
  
 Prowadzi to nam na dwa pytania:  
  
-   Co to jest typ rzeczywistego argumentu `"abc"`?  
  
-   Co to jest algorytm określania, gdy jeden typ konwersji jest lepszym rozwiązaniem niż innego?  
  
 Typ literału ciągu `"abc"` jest `const char[4]` — należy pamiętać, że istnieje niejawna znak zakończenia wartości null na końcu każdej ciągu literału.  
  
 Algorytm określania, gdy jeden typ konwersji jest lepszym rozwiązaniem niż innego obejmuje umieszczenie konwersje typów możliwych w hierarchii. Oto mój opis tej hierarchii — te konwersje są oczywiście niejawnej. Przy użyciu notacji rzutowania jawnego przesłania w sposób podobny do hierarchii nawiasów przesłonięcia zwykle kolejność wyrażenia.  
  
1.  Najlepiej jest dokładnego dopasowania. Zaskakująco argumentu być w pełni zgodne, nie trzeba dokładnie zgodny z typem parametru; po prostu musi być wystarczająco blisko. To jest kluczem do zrozumienia, co dzieje się w tym przykładzie i zmian języka.  
  
2.  Podwyższanie poziomu jest lepszym rozwiązaniem niż konwersja standardowa. Na przykład podwyższania poziomu `short int` do `int` jest lepszym rozwiązaniem niż konwertowanie `int` do `double`.  
  
3.  Konwersja standardowa jest lepszym rozwiązaniem niż konwersji pakującej. Na przykład konwertowanie `int` do `double` działa lepiej, który boxing `int` do `Object`.  
  
4.  Konwersja boxing jest lepszym rozwiązaniem niż niejawna konwersja zdefiniowana przez użytkownika. Na przykład, konwersja boxing `int` do `Object` jest lepszym rozwiązaniem niż zastosowanie operatora konwersji z `SmallInt` klasę wartości.  
  
5.  Niejawna konwersja zdefiniowana przez użytkownika jest lepszym rozwiązaniem niż Brak konwersji w ogóle. Niejawna konwersja zdefiniowana przez użytkownika jest ostatnim zakończenia przed błędu (za pomocą ostrzeżenie, że formalny podpis może zawierać tablicy parametrów i Wielokropek na tej pozycji).  
  
 Tak co oznacza oznacza, że dokładnego dopasowania nie zawsze dokładnie dopasowanie? Na przykład `const char[4]` nie pasuje do żadnej `const char*` lub `String^`, a jeszcze niejednoznaczności naszym przykładzie między dwoma powodujące konflikt dokładne dopasowania!  
  
 Dopasowanie dokładne zdarza się, zawiera wiele trivial konwersji. Istnieją cztery trivial konwersje w C++ ISO, który można zastosować i nadal kwalifikować się jako dokładnego dopasowania. Trzy są określane jako l-wartością przekształcenia. Czwarty typu jest nazywana konwersji kwalifikacji. Trzy przekształcenia l-wartość są traktowane jako lepiej dokładnego dopasowania niż jedno wymaganie konwersji kwalifikacji.  
  
 Jeden formularz transformacji l-wartości jest konwersji native tablicy na wskaźnik. Jest to, na czym polega w odpowiadającym `const char[4]` do `const char*`. W związku z tym dopasowanie `f("abc")` do `f(const char*)` dokładnego dopasowania. W starszych incarnations naszych języka to w rzeczywistości była najlepsze dopasowanie.  
  
 Dla kompilatora, aby flaga wywołań niejednoznaczny, dlatego wymaga konwersji `const char[4]` do `String^` również być dokładnego dopasowania za pomocą prostej konwersji. Jest to zmiana została wprowadzona w nowej wersji językowej. I powoduje to wywołanie jest teraz oznaczony jako niejednoznaczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne zmiany w języku (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [Ciąg](../windows/string-cpp-component-extensions.md)