---
title: Okres istnienia obiektu i zarządzanie zasobami (RAII)
description: Postępuj zgodnie z zasadami RAII w C++ nowoczesne, aby uniknąć przecieków zasobów.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 01867ec0a71ba54bb6534da1b408cb0610d652a7
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303374"
---
# <a name="object-lifetime-and-resource-management-raii"></a>Okres istnienia obiektu i zarządzanie zasobami (RAII)

W przeciwieństwie do języków C++ zarządzanych nie ma automatycznego *wyrzucania elementów bezużytecznych*. Jest to proces wewnętrzny, który zwalnia pamięć sterty i inne zasoby w miarę uruchamiania programu. C++ Program jest odpowiedzialny za zwracanie wszystkich przejętych zasobów do systemu operacyjnego. Niepowodzenie zwolnienia nieużywanego zasobu jest nazywane *wyciekiem*. Przecieki zasobów są niedostępne dla innych programów do momentu zakończenia procesu. Przecieki pamięci w szczególności są typowymi przyczynami błędów w programowaniu w stylu języka C.

Nowoczesne C++ unika korzystanie z pamięci sterty możliwie jak najwięcej przez zadeklarowanie obiektów na stosie. Gdy zasób jest zbyt duży dla stosu, powinien *należeć do* obiektu. Gdy obiekt zostanie zainicjowany, uzyskuje zasób, do którego należy. Obiekt jest następnie odpowiedzialny za zwolnienie zasobu w jego destruktorze. Sam obiekt będący właścicielem jest zadeklarowany na stosie. Zasada, że *obiekty własne* są również znane jako "pozyskiwanie zasobów jest inicjowane" lub RAII.

Gdy obiekt stosu będącego właścicielem zasobu wykracza poza zakres, jego destruktor jest automatycznie wywoływany. W ten sposób wyrzucanie elementów C++ bezużytecznych w programie jest ściśle powiązane z okresem istnienia obiektu i jest deterministyczne. Zasób jest zawsze publikowany w znanym punkcie w programie, który można kontrolować. Tylko deterministyczne destruktory takie jak te C++ w programie mogą jednocześnie obsługiwać pamięć i zasoby niezwiązane z pamięcią.

Poniższy przykład pokazuje prostą `w`obiektu. Jest on zadeklarowany na stosie w zakresie funkcji i jest niszczony na końcu bloku funkcji. Obiekt `w` nie jest właścicielem *zasobów* (takich jak pamięć przydzieloną sterty). Jedyna `g` elementu członkowskiego jest zadeklarowana na stosie i po prostu wykracza poza zakres i `w`. W destruktorze `widget` nie jest wymagany żaden kod specjalny.

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

W poniższym przykładzie `w` jest właścicielem zasobu pamięci i dlatego musi mieć kod w jego destruktorze, aby usunąć pamięć.
 
```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

Ponieważ C++ 11, istnieje lepszy sposób zapisania poprzedniego przykładu: za pomocą inteligentnego wskaźnika z biblioteki standardowej. Inteligentny wskaźnik obsługuje alokację i usunięcie pamięci, do której należy. Użycie inteligentnego wskaźnika eliminuje konieczność jawnego destruktora w klasie `widget`.

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Przy użyciu inteligentnych wskaźników alokacji pamięci można wyeliminować potencjalne przecieki pamięci. Ten model działa w przypadku innych zasobów, takich jak dojścia do plików lub gniazda. Możesz zarządzać własnymi zasobami w podobny sposób w klasach. Aby uzyskać więcej informacji, zobacz [inteligentne wskaźniki](smart-pointers-modern-cpp.md).

Projekt C++ gwarantuje, że obiekty są niszczone, gdy wykraczają poza zakres. Oznacza to, że zostaną zniszczone jako bloki, w odwrotnej kolejności konstrukcji. Gdy obiekt jest niszczony, jego bazy i składowe są niszczone w określonej kolejności. Obiekty zadeklarowane poza blokiem w zakresie globalnym mogą prowadzić do problemów. Debugowanie może być trudne, jeśli Konstruktor obiektu globalnego zgłosi wyjątek.

## <a name="see-also"></a>Zobacz także

[Zapraszamy ponownie doC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
