---
title: "Jawnie ustawiana domyślnie i usunięte funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73e1d52d1c13e2defa51a5cab9da625b75aac757
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Jawnie domyślne i usunięte funkcje
W języku C ++ 11 domyślne i usunięte funkcje mieć jawną kontrolę nad czy specjalnych funkcji Członkowskich są generowane automatycznie. Funkcje usunięte udostępniają prosty język, aby zapobiegać występowaniu problematycznych promocji typu w argumentach funkcji wszystkich typów – zarówno w specjalnych funkcjach członkowskich, jak i w normalnych funkcjach członkowskich oraz funkcjach nieczłonkowskich – które mogą w przeciwnym razie spowodować niechciane wywołania funkcji.  
  
## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Korzyści wynikające z jawnie ustawiana domyślnie i usunięte funkcje  
 W języku C++, kompilator automatycznie generuje konstruktor domyślny, konstruktor kopiujący, operator przypisania kopii oraz destruktor dla typu, jeśli ten nie deklaruje samodzielnie. Funkcje te są nazywane *specjalnych funkcji Członkowskich*, i są one co Tworzenie prostego zdefiniowanych przez użytkownika typów w języku C++ zachowania struktury zrobić w C. Oznacza to można utworzyć, kopiowanie i niszczyć bez dodatkowego kodowania nakładu pracy. W standardzie C++11 dodano do języka przenoszenie semantyki oraz konstruktor przenoszący i operator przypisania przeniesienia do listy specjalnych funkcji członkowskich, które kompilator może wygenerować automatycznie.  
  
 Ta jest przydatna dla typów prostych, ale typy złożone często zdefiniować co najmniej jeden specjalnych funkcji Członkowskich się i to zapobiec innych specjalnych funkcji Członkowskich z automatycznie generowaną. W praktyce:  
  
-   Jeśli dowolny konstruktor jest zadeklarowany w sposób jawny, to żaden domyślny konstruktor nie jest generowany automatycznie.  
  
-   Jeśli destruktor wirtualny jest zadeklarowany w sposób jawny, to żaden domyślny destruktor nie jest generowany automatycznie.  
  
-   Jeśli konstruktor przenoszący lub operator przypisania przeniesienia jest zadeklarowany w sposób jawny, to:  
  
    -   Nie Konstruktor kopiujący jest generowana automatycznie.  
  
    -   Żaden operator przypisania kopiowania jest generowana automatycznie.  
  
-   Jeśli konstruktor kopiujący, operator przypisania kopiowania, konstruktor przeniesienia, operator przypisania przeniesienia lub destruktor jest zadeklarowany w sposób jawny, to:  
  
    -   Żaden konstruktor przenoszenia jest generowana automatycznie.  
  
    -   Żaden operator przypisania przenoszenia jest generowana automatycznie.  
  
> [!NOTE]
>  Ponadto, standard C++11 określa następujące reguły dodatkowe:  
>   
>  -   Jeśli konstruktor kopiujący lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie operatora przypisania kopiowania jest uznawane za przestarzałe.  
> -   Jeśli operator przypisania kopiowania lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie konstruktora kopiującego jest uznawane za przestarzałe.  
>   
>  W obu przypadkach, program Visual Studio kontynuuje automatyczne generowanie niezbędnych funkcji niejawnie i nie emituje ostrzeżenia.  
  
 Konsekwencje tych reguł mogą również wyciec do hierarchii obiektów. Na przykład, jeżeli z jakiegokolwiek powodu klasa podstawowa nie będzie mieć domyślnego konstruktora wywoływanego z klasy pochodnej (to znaczy konstruktora o widoczności `public` lub `protected`, który nie przyjmuje żadnych parametrów), to klasa pochodna nie będzie mogła automatycznie wygenerować własnego konstruktora domyślnego.  
  
 Te reguły skomplikować wykonania co powinna być typy proste, zdefiniowane przez użytkownika i wspólnego idioms C++ — na przykład zapewnienie typu zdefiniowanego przez użytkownika z systemem innym niż copyable przez zadeklarowanie konstruktora kopiującego i operatora przypisania kopii prywatnie, a nie definiując je.  
  
```  
struct noncopyable  
{  
  noncopyable() {};  
  
private:  
  noncopyable(const noncopyable&);  
  noncopyable& operator=(const noncopyable&);  
};  
```  
  
 Przed C ++ 11 następujący fragment kodu była idiomatyczne formę-copyable typów. Ma jednak kilka problemów:  
  
-   Konstruktor kopiujący musi być zadeklarowana prywatnie, aby je ukryć, ale ponieważ jest ona zadeklarowana w ogóle, jest uniemożliwił automatyczne wygenerowanie konstruktora domyślnego. Należy oznaczyć domyślnego konstruktora, jeśli chcesz, nawet jeśli go nie działają.  
  
-   Nawet jeśli jawnie zdefiniowany domyślnego konstruktora nie robi nic, uznaje się nieuproszczony przez kompilator. Jest on mniej skuteczny niż automatycznie generowany konstruktor domyślny i uniemożliwia elementom `noncopyable` bycie prawdziwym typem POD.  
  
-   Nawet jeśli konstruktor kopiujący i operator przypisania kopiowania są ukryte przed kodem zewnętrznym, to funkcje członkowskie i elementy zaprzyjaźnione `noncopyable` nadal mogą je widzieć i wywoływać. Jeśli są one zadeklarowana ale niezdefiniowana, wywołania ich powoduje błąd konsolidatora.  
  
-   Jest to powszechnie zaakceptowany idiom, celem nie jest Wyczyść, chyba że znasz wszystkie reguły do automatycznego generowania specjalnych funkcji Członkowskich.  
  
 W języku C++11 idiom „non-copyable” może być implementowany w sposób, który jest bardziej bezpośredni.  
  
```  
struct noncopyable  
{  
  noncopyable() =default;  
  noncopyable(const noncopyable&) =delete;  
  noncopyable& operator=(const noncopyable&) =delete;  
};  
```  
  
 Powiadomienie jak problemy związane z wstępnie-C ++ 11 idiom zostały rozwiązane:  
  
-   Generowanie konstruktora domyślnego nadal jest uniemożliwiane przez zadeklarowanie konstruktora kopiującego, ale można go przywrócić przez jawne ustawienie go jako domyślnego.  
  
-   Specjalne funkcje członkowskie jawnie ustawione jako domyślne są nadal uważane za trywialne, zatem nie zachodzi pogorszenie wydajności, a elementy `noncopyable` nie są powstrzymywane przed zostaniem prawdziwymi typami POD.  
  
-   Konstruktora kopiującego i operatora przypisania kopii są publiczne, ale został usunięty. Istnieje błąd kompilacji, aby zdefiniować lub wywołać usunięta funkcja.  
  
-   Intencja jest jasna dla każdego, kto rozumie `=default` i `=delete`. Nie trzeba zrozumieć zasady do automatycznego generowania specjalnych funkcji Członkowskich.  
  
 Istnieją podobne idioms dokonywania typy danych zdefiniowane przez użytkownika, które są stałe, który tylko można dynamicznie przydzielić lub że nie można dynamicznie przydzielić. Każdy z tych idioms mieć pre-C ++ 11 implementacje który pogorszyć podobne problemy, a które są rozpoznawane podobnie w języku C ++ 11 zaimplementowanie je w postaci liczby ustawiana domyślnie i usunąć specjalnych funkcji Członkowskich.  
  
## <a name="explicitly-defaulted-functions"></a>Jawnie ustawiana domyślnie funkcji  
 Funkcje Członkowskie specjalne domyślnych — jawnie określić specjalnej funkcji członkowskiej używa Domyślna implementacja, zdefiniuj specjalną funkcją członkowską z kwalifikatorem dostępu publicznego lub przywrócenia członkiem specjalnych funkcji którego automatyczne generowanie uniemożliwiły innych warunkach.  
  
 Specjalną funkcją członkowską jest domyślnie przez zadeklarowanie go jak w poniższym przykładzie:  
  
```  
struct widget  
{  
  widget()=default;  
  
  inline widget& operator=(const widget&);  
};  
  
inline widget& widget::operator=(const widget&) =default;  
```  
  
 Zwróć uwagę, można domyślne specjalną funkcją członkowską poza ciałem klasy tak długo, jak jest inlinable.  
  
 Ze względu na wydajność zalet trivial specjalnych funkcji Członkowskich zalecamy Preferuj automatycznie generowanych specjalnych funkcji Członkowskich przed ciało funkcji jest puste, jeśli chcesz, aby domyślne zachowanie. Można to zrobić, jawnie ustawiając domyślnie specjalnej funkcji członkowskiej, albo nie deklarowanie ją (i również nie deklarowanie innych specjalnych funkcji Członkowskich, które mogłyby uniemożliwiać z automatycznie generowaną.)  
  
## <a name="deleted-functions"></a>Funkcje usunięte  
 Możesz usunąć specjalnych funkcji Członkowskich, a także funkcji Członkowskich normalne i funkcji niebędący elementem członkowskim zapobiegające ich zdefiniowany lub wywołać. Usuwanie specjalnych funkcji Członkowskich umożliwia czyszczący zapobiegania generowania specjalnych funkcji Członkowskich, które nie mają przez kompilator. Funkcja musi zostać usunięta, ponieważ jest przestarzała; dlatego nie może zostać później usunięta w sposób, w jaki została zadeklarowana, a następnie ustawiona jako domyślna.  
  
```  
struct widget  
{  
  // deleted operator new prevents widget from being dynamically allocated.  
  void* operator new(std::size_t) = delete;  
};  
```  
  
 Usuwanie funkcji członkowskiej normalnym lub funkcji nieczłonkowskich zapobiega promocji typu powodować problemy z powoduje niezamierzone funkcja wywoływana. Dzieje się tak, ponieważ funkcje usunięte nadal uczestniczą w wiązaniem i zapewniają lepsze dopasowanie niż funkcji, która może być wywoływana po awansowane typów. Wywołanie funkcji jest rozpoznawane jako funkcja bardziej specyficzna (jednak usunięta) i powoduje błąd kompilatora.  
  
```  
// deleted overload prevents call through type promotion of float to double from succeeding.  
void call_with_true_double_only(float) =delete;  
void call_with_true_double_only(double param) { return; }  
```  
  
 Zauważmy, że w poprzednim przykładzie wywołanie `call_with_true_double_only` przy użyciu argumentu o typie `float` spowodowałoby błąd kompilatora, ale wywołanie `call_with_true_double_only` przy użyciu argumentu o typie `int` nie; w przypadku wartości `int`, argument zostanie promowany z typu `int` do `double` i pomyślnie wywoła funkcję w wersji `double`, nawet jeśli mogło to nie być zamierzone. Aby upewnić się, że każde wywołanie funkcji przy użyciu argumentu o typie innym niż double spowoduje błąd kompilacji, możesz zadeklarować wersję szablonową usuwanej funkcji.  
  
```  
template < typename T >  
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.  
  
void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.  
  
```