---
title: Sample Container — Klasa
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: 404e372e65af8b93ae4f6f2827a73ef64336690a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688973"
---
# <a name="sample-container-class"></a>Sample Container — Klasa

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

Opisuje obiekt, który kontroluje różnej długości sekwencji elementów, zazwyczaj typu `Ty`. Sekwencja jest przechowywana na różne sposoby, w zależności od rzeczywistego kontenera.

Konstruktor kontenera lub funkcja członkowska może odwoływać się do konstruktora **ty**(**const Ty &** ) lub funkcji **ty:: operator =** (**const br &** ). Jeśli takie wywołanie zgłasza wyjątek, obiekt kontenera jest zobowiązany do utrzymania jego integralności i ponownego zgłoszenia wszelkich wyjątków, które wychwytuje. Można bezpiecznie zamienić, przypisać do, wymazać lub zniszczyć obiekt kontenera po wystąpieniu jednego z tych wyjątków. Ogólnie rzecz biorąc, nie można w inny sposób przewidzieć stanu sekwencji kontrolowanej przez obiekt kontenera.

Niektóre dodatkowe zastrzeżenia:

- Jeśli wyrażenie `~Ty` zgłasza wyjątek, stan wynikający z obiektu kontenera jest niezdefiniowany.

- Jeśli kontener przechowuje obiekt alokatora *Al*, a *Al* zgłasza wyjątek inny niż w wyniku wywołania `al.allocate`, wynikowy stan obiektu kontenera jest niezdefiniowany.

- Jeśli kontener przechowuje *zgodność*obiektu funkcji, aby określić sposób uporządkowania kontrolowanej sekwencji, a funkcja *COMP* zgłasza wyjątek dowolnego rodzaju, stan wyniku obiektu kontenera jest niezdefiniowany.

Klasy kontenerów zdefiniowane przez C++ bibliotekę standardową spełniają kilka dodatkowych wymagań, zgodnie z opisem w poniższych akapitach.

[Lista](../standard-library/list-class.md) szablonów klas kontenerów zawiera deterministyczne i przydatne zachowanie, nawet w obecności wyjątków opisanych powyżej. Na przykład, jeśli wyjątek jest zgłaszany podczas wstawiania jednego lub kilku elementów, kontener pozostaje niezmienione i zostanie ponownie zgłoszony wyjątek.

W przypadku *wszystkich* klas kontenerów zdefiniowanych C++ przez bibliotekę Standard, jeśli wyjątek jest zgłaszany podczas wywołań do następujących funkcji składowych, `insert`, `push_back` lub `push_front`, kontener pozostaje niezmienione i ponownie zgłaszany jest wyjątek.

Dla *wszystkich* klas kontenerów zdefiniowanych przez C++ bibliotekę standardową nie jest zgłaszany wyjątek podczas wywołań następujących funkcji członkowskich: `pop_back`, `pop_front`.

Funkcja członkowska [Wymaż](../standard-library/container-class-erase.md) zgłasza wyjątek tylko wtedy, gdy operacja kopiowania (konstrukcja przypisania lub kopiowania) zgłosi wyjątek.

Ponadto żaden wyjątek nie jest zgłaszany podczas kopiowania iteratora zwróconego przez funkcję członkowską.

[Zamiana](../standard-library/container-class-swap.md) funkcji składowej sprawia, że dodatkowe niesie obietnice zwiększenia dla *wszystkich* klas C++ kontenerów zdefiniowanych przez bibliotekę standardową:

- Funkcja członkowska zgłasza wyjątek tylko wtedy, gdy kontener przechowuje obiekt alokatora Al, a `al` zgłasza wyjątek podczas kopiowania.

- Odwołania, wskaźniki i Iteratory, które wyznaczają elementy z wymienianych sekwencji są prawidłowe.

Obiekt klasy kontenera zdefiniowany przez C++ bibliotekę Standard alokuje i zwalnia magazyn dla sekwencji, która kontroluje przez przechowywany obiekt typu `Alloc`, który jest zazwyczaj parametrem szablonu. Taki obiekt alokatora musi mieć ten sam interfejs zewnętrzny co obiekt klasy `allocator<Ty>`. W szczególności `Alloc` muszą być tego samego typu co `Alloc::rebind<value_type>::other`

Dla *wszystkich* klas kontenerów zdefiniowanych C++ przez bibliotekę standardową funkcja członkowska `Alloc get_allocator const;` zwraca kopię przechowywanego obiektu alokatora. Należy zauważyć, że przechowywany obiekt alokatora *nie* jest kopiowany po przypisaniu obiektu kontenera. Wszystkie konstruktory inicjują wartość przechowywaną w `allocator`, aby `Alloc`, jeśli Konstruktor nie zawiera parametru alokatora.

Zgodnie ze C++ standardem, Klasa kontenera zdefiniowana przez bibliotekę C++ standardową może przyjąć, że:

- Wszystkie obiekty klasy `Alloc` porównywane.

- Typ `Alloc::const_pointer` jest taka sama jak `const Ty *`.

- Typ `Alloc::const_reference` jest taka sama jak `const Ty&`.

- Typ `Alloc::pointer` jest taka sama jak `Ty *`.

- Typ `Alloc::reference` jest taka sama jak `Ty&`.

W tej implementacji jednak kontenery nie upraszczają założeń. W ten sposób działają poprawnie z obiektami alokatora, które są bardziej ambitne podejście:

- Wszystkie obiekty klasy `Alloc` nie muszą porównywać wartości równej. (Można zachować wiele pul magazynu).

- Typ `Alloc::const_pointer` nie musi być taki sam jak `const Ty *`. (Stała wskaźnik może być klasą).

- Typ `Alloc::pointer` nie musi być taki sam jak `Ty *`. (Wskaźnik może być klasą).

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<sample kontener >

## <a name="see-also"></a>Zobacz także

[\<sample kontener >](../standard-library/sample-container.md)
