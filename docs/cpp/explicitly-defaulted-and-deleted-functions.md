---
title: Jawnie domyślnych i usuniętych funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69058c00757cea466683246c1aee2e89f806c931
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058617"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Jawnie domyślne i usunięte funkcje

W języku C ++ 11 domyślne i usunięte funkcje umożliwiają jawną kontrolę nad tym, czy specjalne funkcje Członkowskie są generowane automatycznie. Funkcje usunięte udostępniają prosty język, aby zapobiegać występowaniu problematycznych promocji typu w argumentach funkcji wszystkich typów – zarówno w specjalnych funkcjach członkowskich, jak i w normalnych funkcjach członkowskich oraz funkcjach nieczłonkowskich – które mogą w przeciwnym razie spowodować niechciane wywołania funkcji.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Korzyści z jawnie domyślnych i usuniętych funkcji

W języku C++, kompilator automatycznie generuje konstruktor domyślny, konstruktor kopiujący, operator przypisania kopii oraz destruktor dla typu, jeśli ten nie deklaruje samodzielnie. Funkcje te są znane jako *specjalnych funkcji Członkowskich*, i są one, co sprawia, że zdefiniowane przez użytkownika typy proste w języku C++ zachowują się jak struktury w C. Oznacza to można utworzyć, kopiować i niszczyć bez żadnych dodatkowych nakładów pracy kodowania. W standardzie C++11 dodano do języka przenoszenie semantyki oraz konstruktor przenoszący i operator przypisania przeniesienia do listy specjalnych funkcji członkowskich, które kompilator może wygenerować automatycznie.

Jest to wygodne dla typów prostych, ale typy złożone często definiują jedną lub więcej specjalnych funkcji Członkowskich, a może to uniemożliwić innych specjalnych funkcji Członkowskich są generowane automatycznie. W praktyce:

- Jeśli dowolny konstruktor jest zadeklarowany w sposób jawny, to żaden domyślny konstruktor nie jest generowany automatycznie.

- Jeśli destruktor wirtualny jest zadeklarowany w sposób jawny, to żaden domyślny destruktor nie jest generowany automatycznie.

- Jeśli konstruktor przenoszący lub operator przypisania przeniesienia jest zadeklarowany w sposób jawny, to:

   - Żaden Konstruktor kopiujący jest generowany automatycznie.

   - Żaden operator przypisywania kopiowania jest generowany automatycznie.

- Jeśli konstruktor kopiujący, operator przypisania kopiowania, konstruktor przeniesienia, operator przypisania przeniesienia lub destruktor jest zadeklarowany w sposób jawny, to:

   - Żaden konstruktor przenoszący nie jest generowany automatycznie.

   - Żaden operator przypisywania przenoszenia, jest generowany automatycznie.

> [!NOTE]
>  Ponadto, standard C++11 określa następujące reguły dodatkowe:
>
>  -   Jeśli konstruktor kopiujący lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie operatora przypisania kopiowania jest uznawane za przestarzałe.
> -   Jeśli operator przypisania kopiowania lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie konstruktora kopiującego jest uznawane za przestarzałe.
>
>  W obu przypadkach, program Visual Studio kontynuuje automatyczne generowanie niezbędnych funkcji niejawnie i nie emituje ostrzeżenia.

Konsekwencje tych reguł mogą również wyciec do hierarchii obiektów. Na przykład, jeśli z jakiegokolwiek powodu klasa bazowa nie będzie mieć domyślnego konstruktora, który jest wywoływany z Klasa pochodna — oznacza to, że **publicznych** lub **chronione** Konstruktor, który nie przyjmuje żadnych parametrów — następnie klasy który pochodzi od klasy nie może automatycznie wygenerować własnego konstruktora domyślnego.

Te reguły mogą skomplikować Implementowanie tego czymś co powinno być typy proste, zdefiniowane przez użytkownika i wspólnego idiomy języka C++ — na przykład, dzięki czemu typ zdefiniowany przez użytkownika niekopiowalnych przez zadeklarowanie Konstruktor kopiujący i operator przypisania kopiowania, prywatnie i nie Definiowanie ich.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Przed C ++ 11 ten fragment kodu był formą idiomatyczną typów niekopiowalnych. Jednak ma kilka problemów:

- Konstruktor kopiowania musi być zadeklarowany prywatnie, aby je ukryć, ale ponieważ jest on zadeklarowany w ogóle, automatyczne generowanie konstruktora domyślnego nie będzie mógł być. Musisz jawnie zdefiniować Konstruktor domyślny, jeśli chcesz, nawet jeżeli nic nie robi.

- Nawet jeśli jawnie zdefiniowany Konstruktor domyślny nic nie robi, uznaje się nietrywialnymi przez kompilator. Jest on mniej skuteczny niż automatycznie generowany konstruktor domyślny i uniemożliwia elementom `noncopyable` bycie prawdziwym typem POD.

- Nawet jeśli konstruktor kopiujący i operator przypisania kopiowania są ukryte przed kodem zewnętrznym, to funkcje członkowskie i elementy zaprzyjaźnione `noncopyable` nadal mogą je widzieć i wywoływać. Jeśli są one zadeklarowane, ale nie zdefiniowane, wywołanie ich powoduje błąd konsolidatora.

- Chociaż jest to powszechnie akceptowany idiom, zamiar nie jest jasny, chyba że rozumiesz wszystkie reguły do automatycznego generowania funkcji specjalnych elementów członkowskich.

W języku C++11 idiom „non-copyable” może być implementowany w sposób, który jest bardziej bezpośredni.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Zwróć uwagę jak problemy z wstępnie-C ++ 11 idiom zostały rozwiązane:

- Generowanie konstruktora domyślnego nadal jest uniemożliwiane przez zadeklarowanie konstruktora kopiującego, ale można go przywrócić przez jawne ustawienie go jako domyślnego.

- Specjalne funkcje członkowskie jawnie ustawione jako domyślne są nadal uważane za trywialne, zatem nie zachodzi pogorszenie wydajności, a elementy `noncopyable` nie są powstrzymywane przed zostaniem prawdziwymi typami POD.

- Konstruktor kopiujący i operator przydzielania kopii są publiczne, ale zostały usunięte. Jest to błąd kompilacji, aby zdefiniować lub wywoływać funkcję usuniętą.

- Intencja jest jasna dla każdego, kto rozumie `=default` i `=delete`. Nie musisz rozumieć zasad generacji automatycznej funkcji specjalnych elementów członkowskich.

Podobne idiomy do tworzenia typów zdefiniowanych przez użytkownika, które są nieruchome, który tylko można dynamicznie przydzielić lub którego nie można przydzielać dynamicznie. Każdy z tych idiomy mieć pre-C ++ 11 implementacje których występują podobne problemy i są podobnie rozwiązane w C ++ 11, wdrażając je na podstawie domyślnych i usuniętych funkcji specjalnych elementów członkowskich.

## <a name="explicitly-defaulted-functions"></a>Funkcje jawnie przyjmujące wartości domyślne

Domyślne dowolne specjalne funkcje Członkowskie — Aby jawnie określać, że specjalna funkcja członkowska używa implementacji domyślnej, określić specjalną funkcję członkowską z kwalifikatorem dostęp publiczny lub przywrócić specjalnych elementów członkowskich z których funkcji Automatyczna generacja została uniemożliwiona przez inne okoliczności.

Ustawiasz jako domyślną specjalną funkcję członkowską deklarując ją jak w poniższym przykładzie:

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Należy zauważyć, że można ustawić domyślną specjalną funkcję członkowską poza treścią klasy tak długo, jak jest możliwa do wbudowania.

Ze względu na korzyści dotyczących wydajności trivial specjalnych funkcji Członkowskich firma Microsoft zaleca preferowanie automatycznie generowanych specjalne funkcje Członkowskie za pośrednictwem ciało funkcji jest puste, jeśli chcesz, zachowanie domyślne. Można to zrobić, ustawiając jako domyślną specjalną funkcję członkowską, albo nie deklarując jej (i również nie deklarując innych specjalnych funkcji Członkowskich, które uniemożliwiałyby jej automatyczne generowanie)

## <a name="deleted-functions"></a>Funkcje usunięte

Można usunąć specjalne funkcje Członkowskie, a także normalnych funkcjach Członkowskich oraz funkcjach nieczłonkowskich – zapobiegające je lub nazywaniu. Usuwanie specjalnych funkcji Członkowskich zapewnia bardziej przejrzysty sposób zapobiegania generowaniu przez kompilatora z generowania funkcji specjalnych elementów członkowskich, które nie mają. Funkcja musi zostać usunięta, ponieważ jest przestarzała; dlatego nie może zostać później usunięta w sposób, w jaki została zadeklarowana, a następnie ustawiona jako domyślna.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

Usuwanie normalnej funkcji członkowskiej lub nieczłonkowskiej zapobiega problematycznym promocjom spowodowanym powoduje niezamierzone funkcja do wywołania. To działa, ponieważ usunięte funkcje nadal uczestniczy w przeciążeniu rozdzielczości i zapewniają lepsze dopasowane niż funkcja, która może być wywoływana po wypromowaniu typów. Wywołanie funkcji jest rozpoznawane jako funkcja bardziej specyficzna (jednak usunięta) i powoduje błąd kompilatora.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

Należy zauważyć w poprzednim przykładzie, że wywołanie `call_with_true_double_only` przy użyciu **float** argument spowodowałoby błąd kompilatora, ale wywołanie `call_with_true_double_only` przy użyciu **int** argument może nie; w **int** przypadku argument zostanie promowany z **int** do **double** i pomyślnie wywoła **double** wersja tej funkcji, Mimo że może nie być zamierzone. Aby upewnić się, że każde wywołanie funkcji przy użyciu argumentu o typie innym niż double spowoduje błąd kompilacji, możesz zadeklarować wersję szablonową usuwanej funkcji.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```