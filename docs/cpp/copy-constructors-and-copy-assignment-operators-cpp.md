---
title: Konstruktory kopiujące i kopiujące operatory przypisania (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: beabe4c6219975d33c7af98a94498188c9abfa55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189535"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Konstruktory kopiujące i kopiujące operatory przypisania (C++)

> [!NOTE]
> Począwszy od języka C++ 11, obsługiwane są dwa rodzaje przypisywania w języku: *Kopiuj przypisanie* i *Przenieś przypisanie*. W tym artykule "przypisanie" oznacza przypisanie kopiowania, chyba że wyraźnie określono inaczej. Informacje o przypisywaniu przenoszenia znajdują się w temacie [przenoszenie konstruktorówC++i operatory przypisania przenoszenia ()](move-constructors-and-move-assignment-operators-cpp.md).
>
> Zarówno operacja przypisania, jak i operacja inicjowania powodują, że obiekty mają być kopiowane.

- **Przypisanie**: gdy wartość jednego obiektu jest przypisana do innego obiektu, pierwszy obiekt jest kopiowany do drugiego obiektu. Zatem

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   powoduje, że wartość `b` ma być kopiowana do `a`.

- **Inicjalizacja**: inicjalizacja występuje, gdy jest zadeklarowany nowy obiekt, gdy argumenty są przenoszone do funkcji przez wartość lub gdy wartości są zwracane z funkcji przez wartość.

Można zdefiniować semantykę "Copy" dla obiektów typu klasy. Na przykład, rozważmy ten kod:

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

Poprzedni kod może oznaczać "Kopiowanie zawartości plik1. DAT do PLIK2. DAT "lub może oznaczać" ignorowanie PLIK2. DAT i wprowadź `b` drugim dojściem do plik1. DAT. " Należy dołączyć odpowiednie semantyke kopiowania do każdej klasy w następujący sposób.

- Używając operatora operatora przypisania **=** wraz z odwołaniem do typu klasy jako zwracany typ i parametr, który jest przesyłany przez odwołanie **const** , na przykład `ClassName& operator=(const ClassName& x);`.

- Za pomocą konstruktora kopiującego.

Jeśli Konstruktor kopiujący nie zostanie zadeklarowany, kompilator generuje dla Ciebie Konstruktor kopiujący.  Jeśli operator przypisania kopiowania nie zostanie zadeklarowany, kompilator generuje dla Ciebie operatora przypisania kopii dla elementu członkowskiego. Deklarowanie konstruktora kopiującego nie powoduje pomijania operatora przypisania kopii generowanego przez kompilator ani odwrotnie. W przypadku zaimplementowania jednego z nich zalecamy także zaimplementowanie drugiego, tak aby znaczenie kodu było jasne.

Konstruktor kopiujący przyjmuje argument typu <em>class-name</em> <strong>&</strong>, gdzie *class-name* to nazwa klasy, dla której jest zdefiniowany Konstruktor. Na przykład:

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> Zmień typ argumentu konstruktora kopiującego na wartość **const** <em>class-name</em> <strong>&</strong> , jeśli to możliwe. Zapobiega to przypadkowemu zmianie obiektu, z którego jest kopiowany przez konstruktora kopiującego. Umożliwia również kopiowanie z obiektów **const** .

## <a name="compiler-generated-copy-constructors"></a>Konstruktory kopiujące wygenerowane przez kompilator

Konstruktory kopiujące generowane przez kompilator, takie jak konstruktory kopiowania zdefiniowane przez użytkownika, mają pojedynczy argument typu "odwołanie do *nazwy klasy*". Wyjątek polega na tym, że wszystkie klasy bazowe i klasy składowe mają konstruktory kopiujące zadeklarowane jako przyjmujące pojedynczy argument typu **const** <em>class-name</em> <strong>&</strong>. W takim przypadku argument konstruktora kopiującego generowany przez kompilator jest również wartością **const**.

Gdy typ argumentu konstruktora kopiującego nie jest wartością **stałą**, inicjowanie przez skopiowanie obiektu **const** generuje błąd. Odwrócenie nie jest prawdziwe: Jeśli argument jest **stałą**, można zainicjować przez skopiowanie obiektu, który nie jest **stałą**.

Operatory przypisania generowane przez kompilator stosują ten sam wzorzec w odniesieniu do **const.** Przyjmuje jeden argument typu <em>class-name</em> <strong>&</strong> , chyba że operatory przypisania we wszystkich klasach bazowych i Członkowskich nie przyjmują argumentów typu **const** <em>class-name</em> <strong>&</strong>. W takim przypadku generowany operator przypisania klasy przyjmuje argument **const** .

> [!NOTE]
> Gdy wirtualne klasy bazowe są inicjowane przez konstruktory kopiujące, generowane przez kompilator lub zdefiniowane przez użytkownika, są inicjowane tylko raz: w momencie ich konstruowania.

Konsekwencje są podobne do tych w konstruktorze kopiującym. Gdy typ argumentu nie jest **stałą**, przypisanie z obiektu **const** generuje błąd. Odwrócenie nie jest prawdziwe: Jeśli wartość **stała** jest przypisana do wartości, która nie jest **stałą**, przypisanie zakończy się pomyślnie.

Aby uzyskać więcej informacji o przeciążonych operatorach przypisania, zobacz [przypisanie](../cpp/assignment.md).
