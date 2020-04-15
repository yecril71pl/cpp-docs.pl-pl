---
title: Jawnie domyślne i usunięte funkcje
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: bd13b5fef3a9dfc13d72f1ee34d7ced902735e15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360904"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Jawnie domyślne i usunięte funkcje

W języku C++11 domyślne i usunięte funkcje zapewniają wyraźną kontrolę nad tym, czy funkcje specjalne elementy członkowskie są generowane automatycznie. Funkcje usunięte udostępniają prosty język, aby zapobiegać występowaniu problematycznych promocji typu w argumentach funkcji wszystkich typów – zarówno w specjalnych funkcjach członkowskich, jak i w normalnych funkcjach członkowskich oraz funkcjach nieczłonkowskich – które mogą w przeciwnym razie spowodować niechciane wywołania funkcji.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Korzyści z jawnie domyślnych i usuniętych funkcji

W języku C++, kompilator automatycznie generuje konstruktor domyślny, konstruktor kopiujący, operator przypisania kopii oraz destruktor dla typu, jeśli ten nie deklaruje samodzielnie. Funkcje te są znane jako *funkcje elementów członkowskich specjalnych*i są one, co sprawiają, że proste typy zdefiniowane przez użytkownika w języku C++ zachowują się jak struktury zrobić w języku C. Oznacza to, że można je tworzyć, kopiować i niszczyć bez dodatkowego wysiłku kodowania. W standardzie C++11 dodano do języka przenoszenie semantyki oraz konstruktor przenoszący i operator przypisania przeniesienia do listy specjalnych funkcji członkowskich, które kompilator może wygenerować automatycznie.

Jest to wygodne dla typów prostych, ale typy złożone często definiują jedną lub więcej funkcji specjalnych elementów członkowskich, a to może uniemożliwić automatyczne generowanie innych specjalnych funkcji członkowskich. W praktyce:

- Jeśli dowolny konstruktor jest zadeklarowany w sposób jawny, to żaden domyślny konstruktor nie jest generowany automatycznie.

- Jeśli destruktor wirtualny jest zadeklarowany w sposób jawny, to żaden domyślny destruktor nie jest generowany automatycznie.

- Jeśli konstruktor przenoszący lub operator przypisania przeniesienia jest zadeklarowany w sposób jawny, to:

  - Konstruktor kopii nie jest generowany automatycznie.

  - Operator przypisania kopii nie jest generowany automatycznie.

- Jeśli konstruktor kopiujący, operator przypisania kopiowania, konstruktor przeniesienia, operator przypisania przeniesienia lub destruktor jest zadeklarowany w sposób jawny, to:

  - Konstruktor ruchu nie jest generowany automatycznie.

  - Żaden operator przypisania przenoszenia nie jest generowany automatycznie.

> [!NOTE]
> Ponadto, standard C++11 określa następujące reguły dodatkowe:
>
> - Jeśli konstruktor kopiujący lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie operatora przypisania kopiowania jest uznawane za przestarzałe.
> - Jeśli operator przypisania kopiowania lub destruktor jest zadeklarowany w sposób jawny, to automatyczne generowanie konstruktora kopiującego jest uznawane za przestarzałe.
>
> W obu przypadkach, program Visual Studio kontynuuje automatyczne generowanie niezbędnych funkcji niejawnie i nie emituje ostrzeżenia.

Konsekwencje tych reguł mogą również wyciec do hierarchii obiektów. Na przykład jeśli z jakiegokolwiek powodu klasa podstawowa nie ma domyślnego konstruktora, który jest wywoływany z klasy pochodnej , czyli konstruktora **publicznego** lub **chronionego,** który nie przyjmuje żadnych parametrów — wówczas klasa, która z niej pochodzi, nie może automatycznie wygenerować własnego domyślnego konstruktora.

Reguły te mogą skomplikować implementację tego, co powinno być proste, zdefiniowane przez użytkownika typy i wspólne idiomy języka C++ — na przykład uczynienie typu zdefiniowanego przez użytkownika niekopialnym, deklarując konstruktora kopii i operatora przypisywania kopii prywatnie i nie definiując ich.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Przed C++ 11 ten fragment kodu był idiomatyczną formą typów niekopywalnych. Jednak ma kilka problemów:

- Konstruktor kopii musi być zadeklarowany prywatnie, aby go ukryć, ale ponieważ jest zadeklarowany w ogóle, automatyczne generowanie konstruktora domyślnego jest zapobiegana. Musisz jawnie zdefiniować konstruktora domyślnego, jeśli chcesz, nawet jeśli nic nie robi.

- Nawet jeśli jawnie zdefiniowany konstruktor domyślny nic nie robi, jest uważany za nietrywialny przez kompilator. Jest on mniej skuteczny niż automatycznie generowany konstruktor domyślny i uniemożliwia elementom `noncopyable` bycie prawdziwym typem POD.

- Nawet jeśli konstruktor kopiujący i operator przypisania kopiowania są ukryte przed kodem zewnętrznym, to funkcje członkowskie i elementy zaprzyjaźnione `noncopyable` nadal mogą je widzieć i wywoływać. Jeśli są one zadeklarowane, ale nie zdefiniowane, wywołanie ich powoduje błąd konsolidatora.

- Chociaż jest to powszechnie akceptowany idiom, intencja nie jest jasne, chyba że rozumiesz wszystkie reguły automatycznego generowania funkcji specjalnych elementów członkowskich.

W języku C++11 idiom „non-copyable” może być implementowany w sposób, który jest bardziej bezpośredni.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Zwróć uwagę, jak problemy z pre-C ++ 11 idiom są rozwiązywane:

- Generowanie konstruktora domyślnego nadal jest uniemożliwiane przez zadeklarowanie konstruktora kopiującego, ale można go przywrócić przez jawne ustawienie go jako domyślnego.

- Specjalne funkcje członkowskie jawnie ustawione jako domyślne są nadal uważane za trywialne, zatem nie zachodzi pogorszenie wydajności, a elementy `noncopyable` nie są powstrzymywane przed zostaniem prawdziwymi typami POD.

- Konstruktor kopii i operator przypisania kopii są publiczne, ale usunięte. Jest to błąd w czasie kompilacji, aby zdefiniować lub wywołać usuniętą funkcję.

- Intencja jest jasna dla każdego, kto rozumie `=default` i `=delete`. Nie musisz rozumieć reguł automatycznego generowania specjalnych funkcji członkowskich.

Podobne idiomy istnieją do tworzenia typów zdefiniowanych przez użytkownika, które nie są ruchome, które mogą być przydzielane tylko dynamicznie lub które nie mogą być przydzielane dynamicznie. Każdy z tych idiomów mają pre-C ++ 11 implementacje, które cierpią podobne problemy i które są podobnie rozwiązane w języku C ++ 11, implementując je pod względem domyślnych i usuniętych funkcji specjalnych elementów członkowskich.

## <a name="explicitly-defaulted-functions"></a>Jawnie domyślne funkcje

Można domyślnie dowolną z funkcji specjalnych elementów członkowskich — jawnie stwierdzić, że funkcja specjalnego elementu członkowskiego używa domyślnej implementacji, do definiowania funkcji specjalnego elementu członkowskiego z kwalifikatorem dostępu niepublicznego lub przywrócenia funkcji specjalnego elementu członkowskiego, której automatyczne generowanie zostało uniemożliwione przez inne okoliczności.

Domyślnie funkcja specjalnego elementu członkowskiego, deklarując ją w następujący sposób w tym przykładzie:

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Należy zauważyć, że można domyślnie funkcji elementu członkowskiego specjalne poza treścią klasy, tak długo, jak jest to nieosiągalne.

Ze względu na korzyści z wydajności trywialne funkcje specjalne elementów członkowskich, zaleca się, aby automatycznie generowane funkcje specjalne elementów członkowskich nad pustymi organami funkcji, gdy chcesz zachowanie domyślne. Można to zrobić, jawnie domyślnie funkcji elementu członkowskiego specjalnych lub nie deklarując go (a także nie deklarując innych funkcji specjalnych elementów członkowskich, które uniemożliwiłyby jej automatyczne generowanie.)

## <a name="deleted-functions"></a>Usunięte funkcje

Można usunąć specjalne funkcje członkowskie, a także normalne funkcje członkowskie i funkcje niebędące członkami, aby zapobiec ich definiowaniu lub wywoływaniu. Usuwanie funkcji specjalnych elementów członkowskich zapewnia czystszy sposób zapobiegania kompilatorowi generowania specjalnych funkcji członkowskich, które nie są żądane. Funkcja musi zostać usunięta, ponieważ jest przestarzała; dlatego nie może zostać później usunięta w sposób, w jaki została zadeklarowana, a następnie ustawiona jako domyślna.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

Usunięcie funkcji normalnego elementu członkowskiego lub funkcji niebędących członkami zapobiega problematycznym promocjom typu powodującym wywołanie niezamierzonej funkcji. Działa to, ponieważ usunięte funkcje nadal uczestniczą w rozpoznawaniu przeciążenia i zapewniają lepsze dopasowanie niż funkcja, która może być wywoływana po promowaniu typów. Wywołanie funkcji jest rozpoznawane jako funkcja bardziej specyficzna (jednak usunięta) i powoduje błąd kompilatora.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

Uwaga w poprzednim przykładzie, że wywołanie `call_with_true_double_only` przy użyciu argumentu `call_with_true_double_only` **float** spowodowałoby błąd kompilatora, ale wywołanie przy użyciu argumentu **int** nie będzie; w przypadku **int** argument zostanie podniesiony z **int** do **double** i pomyślnie wywołać **podwójną** wersję funkcji, nawet jeśli nie może być to, co jest zamierzone. Aby upewnić się, że każde wywołanie tej funkcji przy użyciu argumentu non-double powoduje błąd kompilatora, można zadeklarować wersję szablonu funkcji, która jest usuwana.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```
