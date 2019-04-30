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
ms.openlocfilehash: 59f463d103e233a1d9b25da3243a16f67263c815
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392300"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Konstruktory kopiujące i kopiujące operatory przypisania (C++)

> [!NOTE]
> Począwszy od C ++ 11, dwa rodzaje przypisania są obsługiwane w języku: *przypisania kopiowania* i *Przenieś przypisania*. W tym artykule "przypisania" oznacza przypisania kopiowania, chyba że wyraźnie określono inaczej. Aby uzyskać informacji na temat przypisania przeniesienia, zobacz [konstruktory przenoszenia i operatory przenoszenia przypisania (C++)](move-constructors-and-move-assignment-operators-cpp.md).
>
> Operacja przypisania i z operację zainicjowanie spowodować obiekty do skopiowania.

- **Przypisanie**: Gdy wartość jeden obiekt jest przypisany do innego obiektu, pierwszy obiekt jest kopiowany do drugiego obiektu. W związku z tym,

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   powoduje, że wartość `b` do skopiowania do `a`.

- **Inicjowanie**: Inicjalizacja występuje, gdy nowy obiekt jest zadeklarowana, gdy argumenty są przekazywane do funkcji przez wartość lub wartości są zwracane przez funkcje według wartości.

Można zdefiniować semantykę "Kopiuj" dla obiektów typu klasy. Na przykład, rozważmy ten kod:

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

Powyższy kod może oznaczać, że "skopiuj zawartość Plik1. DAT, aby Plik2. DAT"lub jest on może oznaczać, że"ignorowania Plik2. DAT i `b` drugi dojścia do FILE1.DAT. " Odpowiednie semantyki kopiowania należy dołączyć do każdej klasy, w następujący sposób.

- Za pomocą operatora przypisania **operator =** wraz z odwołaniem do typu klasy jako zwracany typ i parametr, który jest przekazywany przez **const** odwołania — na przykład `ClassName& operator=(const ClassName& x);`.

- Za pomocą konstruktora kopiującego.

Jeśli nie deklaruj konstruktora kopiującego, kompilator generuje konstruktora kopiującego member-wise dla Ciebie.  Jeśli nie deklaruj operator przypisania kopii, kompilator generuje operatora przypisanej kopii member-wise dla Ciebie. Zadeklarowanie konstruktora kopiującego nie pomija operator przypisania kopiowania generowanych przez kompilator, ani na odwrót. W przypadku zastosowania pojedynczo, firma Microsoft zaleca również Implementowanie innego tak, aby znaczenia kodu jest wyczyszczone.

Konstruktor kopiujący przyjmuje argument typu <em>Nazwa klasy</em><strong>&</strong>, gdzie *Nazwa klasy* jest nazwa klasy, dla którego zdefiniowano konstruktora. Na przykład:

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
> Zmień typ argumentu konstruktora kopiującego **const** <em>Nazwa klasy</em> <strong>&</strong> zawsze, gdy jest to możliwe. Zapobiega to przypadkowym zmianom obiektu, z którego jest kopiowanie konstruktora kopiującego. Umożliwia także skopiowanie **const** obiektów.

## <a name="compiler-generated-copy-constructors"></a>Konstruktory kopiujące wygenerowanego przez kompilator

Konstruktory kopiujące generowanych przez kompilator, takich jak konstruktorów kopiujących zdefiniowanych przez użytkownika mają pojedynczy argument typu "odwołanie do *Nazwa klasy*." Jest wyjątek, jeśli wszystkie klasy podstawowe i element członkowski klasy konstruktorów kopiujących zadeklarowane jako pojedynczy argument typu biorąc **const** <em>Nazwa klasy</em><strong>&</strong>. W takim przypadku argument Konstruktor kopiujący wygenerowany przez kompilator jest również **const**.

Gdy typ argumentu do konstruktora kopiującego nie jest **const**, inicjowanie, kopiując **const** obiektu spowoduje wygenerowanie błędu. Odwrotnej nie jest spełniony: Jeśli argument jest **const**, można zainicjować przez skopiowanie obiektu, który nie jest **const**.

Operatory przypisania generowane przez kompilator, należy wykonać w odniesieniu do tego samego wzorca **const.** Przyjmują jeden argument typu <em>Nazwa klasy</em> <strong>&</strong> , chyba że operatory przypisania w wszystkie klasy podstawowe i składowe przyjmują argumenty typu **const** <em>Nazwa klasy</em><strong>&</strong>. W tym przypadku klasy użytkownika generowany przyjmuje operatora przypisania **const** argumentu.

> [!NOTE]
> Gdy wirtualne klasy bazowe są inicjowane przez konstruktory kopiujące, generowane przez kompilator lub zdefiniowanych przez użytkownika są inicjowanie tylko raz: w momencie, gdy zostały skonstruowane.

Implikacje są podobne do występujących dla konstruktora kopiującego. Gdy typ argumentu nie jest **const**, przypisanie z **const** obiektu spowoduje wygenerowanie błędu. Odwrotnej nie jest spełniony: Jeśli **const** wartość jest przypisywana wartość, która nie jest **const**, przypisanie zakończy się pomyślnie.

Aby uzyskać więcej informacji na temat przypisania przeciążone operatory zobacz [przypisania](../cpp/assignment.md).