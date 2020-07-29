---
title: Jawnie domyślne i usunięte funkcje
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: fd3fb53dec0cc08274b7ea54176c2a15dbab45d7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211583"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Jawnie domyślne i usunięte funkcje

W języku C++ 11 funkcje domyślne i usunięte zapewniają jawną kontrolę nad tym, czy specjalne funkcje członkowskie są generowane automatycznie. Funkcje usunięte udostępniają prosty język, aby zapobiegać występowaniu problematycznych promocji typu w argumentach funkcji wszystkich typów – zarówno w specjalnych funkcjach członkowskich, jak i w normalnych funkcjach członkowskich oraz funkcjach nieczłonkowskich – które mogą w przeciwnym razie spowodować niechciane wywołania funkcji.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Zalety funkcji jawnie domyślnych i usuniętych

W języku C++, kompilator automatycznie generuje konstruktor domyślny, konstruktor kopiujący, operator przypisania kopii oraz destruktor dla typu, jeśli ten nie deklaruje samodzielnie. Te funkcje są znane jako *specjalne funkcje składowe*i są, co sprawia, że proste typy zdefiniowane przez użytkownika w języku C++ zachowują się jak struktury w C. Oznacza to, że można je tworzyć, kopiować i niszczyć bez dodatkowych nakładów związanych z programowaniem. W standardzie C++11 dodano do języka przenoszenie semantyki oraz konstruktor przenoszący i operator przypisania przeniesienia do listy specjalnych funkcji członkowskich, które kompilator może wygenerować automatycznie.

Jest to wygodne dla typów prostych, ale typy złożone często definiują co najmniej jedną specjalną funkcję członkowską i może to uniemożliwić automatyczne generowanie innych specjalnych funkcji Członkowskich. W ramach ćwiczenia:

- Jeśli dowolny konstruktor jest zadeklarowany w sposób jawny, to żaden domyślny konstruktor nie jest generowany automatycznie.

- Jeśli destruktor wirtualny jest zadeklarowany w sposób jawny, to żaden domyślny destruktor nie jest generowany automatycznie.

- Jeśli konstruktor przenoszący lub operator przypisania przeniesienia jest zadeklarowany w sposób jawny, to:

  - Żaden Konstruktor kopiujący nie jest generowany automatycznie.

  - Żaden operator przypisania kopii nie jest generowany automatycznie.

- Jeśli konstruktor kopiujący, operator przypisania kopiowania, konstruktor przeniesienia, operator przypisania przeniesienia lub destruktor jest zadeklarowany w sposób jawny, to:

  - Konstruktor przenoszący nie jest generowany automatycznie.

  - Nie jest generowany automatycznie żaden operator przypisania przenoszenia.

> [!NOTE]
> Ponadto, standard C++11 określa następujące reguły dodatkowe:
>
> - Jeśli konstruktor kopiujący lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie operatora przypisania kopiowania jest uznawane za przestarzałe.
> - Jeśli operator przypisania kopiowania lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie konstruktora kopiującego jest uznawane za przestarzałe.
>
> W obu przypadkach, program Visual Studio kontynuuje automatyczne generowanie niezbędnych funkcji niejawnie i nie emituje ostrzeżenia.

Konsekwencje tych reguł mogą również wyciec do hierarchii obiektów. Na przykład, jeśli z jakiegokolwiek powodu Klasa bazowa nie może mieć domyślnego konstruktora, który jest wywoływany z klasy pochodnej, czyli **`public`** konstruktora lub, **`protected`** który nie przyjmuje parametrów, a następnie Klasa, która dziedziczy z niej, nie może automatycznie wygenerować własnego domyślnego konstruktora.

Te reguły mogą komplikują implementację elementów, które powinny być typu prostego, zdefiniowane przez użytkownika i wspólną idiomy języka C++ — na przykład, aby typ zdefiniowany przez użytkownika nie mógł być kopiowany przez zadeklarowanie konstruktora kopiującego i operatora przypisania kopiowania w sposób prywatny i niedefiniujący.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Przed C++ 11 ten fragment kodu był idiomatyczne formą typów nienależących do kopiowania. Występuje jednak kilka problemów:

- Konstruktor kopiujący musi być zadeklarowany prywatnie, aby go ukryć, ale ponieważ został zadeklarowany w całości, automatyczne generowanie domyślnego konstruktora jest uniemożliwione. Musisz jawnie zdefiniować Konstruktor domyślny, jeśli chcesz, nawet jeśli nie robi nic.

- Nawet jeśli jawnie zdefiniowany Konstruktor domyślny nie robi nic, jest traktowany jako nieuproszczony przez kompilator. Jest on mniej skuteczny niż automatycznie generowany konstruktor domyślny i uniemożliwia elementom `noncopyable` bycie prawdziwym typem POD.

- Nawet jeśli konstruktor kopiujący i operator przypisania kopiowania są ukryte przed kodem zewnętrznym, to funkcje członkowskie i elementy zaprzyjaźnione `noncopyable` nadal mogą je widzieć i wywoływać. Jeśli są one zadeklarowane, ale nie zdefiniowane, wywołanie ich powoduje błąd konsolidatora.

- Chociaż jest to powszechnie akceptowane idiom, zamiar nie jest jasne, chyba że rozumiesz wszystkie reguły automatycznego generowania specjalnych funkcji Członkowskich.

W języku C++11 idiom „non-copyable” może być implementowany w sposób, który jest bardziej bezpośredni.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Zwróć uwagę na to, jak rozwiązywane są problemy z idiommi pre-C + + 11:

- Generowanie konstruktora domyślnego nadal jest uniemożliwiane przez zadeklarowanie konstruktora kopiującego, ale można go przywrócić przez jawne ustawienie go jako domyślnego.

- Specjalne funkcje członkowskie jawnie ustawione jako domyślne są nadal uważane za trywialne, zatem nie zachodzi pogorszenie wydajności, a elementy `noncopyable` nie są powstrzymywane przed zostaniem prawdziwymi typami POD.

- Konstruktor kopiujący i operator przypisania kopiowania są publiczne, ale usuwane. Jest to błąd czasu kompilacji służący do definiowania lub wywoływania usuniętej funkcji.

- Intencja jest jasna dla każdego, kto rozumie `=default` i `=delete`. Nie trzeba zrozumieć reguł automatycznego generowania specjalnych funkcji Członkowskich.

Podobne idiomy istnieją do tworzenia typów zdefiniowanych przez użytkownika, które nie są przenośne, które mogą być przydzielane dynamicznie lub nie mogą być przydzielane dynamicznie. Każdy z tych idiomy ma implementacje pre-C + + 11, które odnoszą się do podobnych problemów i są podobnie rozwiązane w języku C++ 11 przez implementację ich w postaci domyślnych i usuniętych specjalnych funkcji Członkowskich.

## <a name="explicitly-defaulted-functions"></a>Jawnie domyślne funkcje

Można domyślnie dowolnie dowolnych specjalnych funkcji składowych — aby jawnie określić, że Specjalna funkcja członkowska korzysta z implementacji domyślnej, do definiowania specjalnej funkcji składowej z kwalifikatorem niepublicznego dostępu lub do przywracania specjalnej funkcji składowej, której automatyczne generowanie zostało uniemożliwione przez inne okoliczności.

Domyślnie Specjalna funkcja członkowska deklaruje ją jak w poniższym przykładzie:

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Należy zauważyć, że można domyślnie wykonać specjalną funkcję członkowską poza treścią klasy, o ile jest to wbudowania.

Ze względu na wydajność zalet prostych specjalnych funkcji składowych zaleca się, aby automatycznie generować specjalne funkcje członkowskie dla pustych jednostek funkcji, gdy ma to zastosowanie. Można to zrobić przez jawne ustawienie specjalnej funkcji składowej lub niedeklarowanie jej (a także niedeklarowanie innych specjalnych funkcji Członkowskich, które uniemożliwią automatyczne wygenerowanie.)

## <a name="deleted-functions"></a>Funkcje usunięte

Można usunąć specjalne funkcje składowe, a także normalne funkcje członkowskie i funkcje nieczłonkowskie, aby zapobiec ich zdefiniowaniu lub wywołaniu. Usuwanie specjalnych funkcji Członkowskich zapewnia przejrzysty sposób uniemożliwiający kompilatorowi generowanie specjalnych funkcji Członkowskich, które nie są potrzebne. Funkcja musi zostać usunięta, ponieważ jest przestarzała; dlatego nie może zostać później usunięta w sposób, w jaki została zadeklarowana, a następnie ustawiona jako domyślna.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

Usunięcie normalnej funkcji składowej lub funkcji nienależących do elementów członkowskich zapobiega wywoływaniu nieoczekiwanych funkcji. Dzieje się tak, ponieważ usunięte funkcje nadal uczestniczą w rozwiązywaniu przeciążenia i zapewniają lepszą zgodność niż funkcja, która może być wywoływana po podwyższeniu poziomu. Wywołanie funkcji jest rozpoznawane jako funkcja bardziej specyficzna (jednak usunięta) i powoduje błąd kompilatora.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

Zwróć uwagę na poprzedni przykład, który wywołuje przy `call_with_true_double_only` użyciu **`float`** argumentu, powoduje błąd kompilatora, ale wywołanie przy `call_with_true_double_only` użyciu **`int`** argumentu nie; w **`int`** przypadku, argument zostanie podwyższony z **`int`** do **`double`** i pomyślnie wywoła **`double`** wersję funkcji, nawet jeśli nie jest to zamierzone. Aby upewnić się, że każde wywołanie tej funkcji przy użyciu argumentu niepodwójnego powoduje błąd kompilatora, można zadeklarować wersję szablonu funkcji, która jest usuwana.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```
