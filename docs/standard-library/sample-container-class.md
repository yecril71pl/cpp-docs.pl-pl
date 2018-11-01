---
title: Sample Container — Klasa
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: dbfa076756b9e4829898d38e0277ad90106ba579
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536230"
---
# <a name="sample-container-class"></a>Sample Container — Klasa

> [!NOTE]
> Ten temat dotyczy w dokumentacji języka Visual C++ jako prawidłowo przykład kontenerów używanych w standardowej biblioteki języka C++. Aby uzyskać więcej informacji, zobacz [standardowych kontenerów biblioteki języka C++](../standard-library/stl-containers.md).

Opisuje obiekt, który kontroluje różnej długości sekwencje elementów typu zazwyczaj `Ty`. Sekwencja jest przechowywany na różne sposoby, w zależności od rzeczywistej kontenera.

Funkcja konstruktora lub elementu członkowskiego kontenera może się okazać razem, gdy wywołanie konstruktora **Ty**(**const Ty &**) lub funkcja **Ty::operator =**(**const Ty &**). Jeśli takie wywołanie zgłasza wyjątek, obiekt kontenera jest zobowiązany do utrzymanie integralności i aby można było ponownie każdy wyjątek, który przechwytuje. Możesz bezpiecznie wymiany, przypisz do wymazania lub zniszczenia obiektu kontenera po zgłasza wyjątek, jeden z tych wyjątków. Ogólnie rzecz biorąc jednak nie może w przeciwnym razie przewidzieć stanu na sekwencję kontrolowaną przez obiekt kontenera.

Kilka dodatkowych ostrzeżenia:

- Jeśli wyrażenie `~Ty` zgłasza wyjątek, który, stan wynikowy obiekt kontenera jest niezdefiniowana.

- Jeśli kontener przechowywany obiekt alokatora *al*, i *al* zgłasza wyjątek innych niż w wyniku wywołania `al.allocate`, stan wynikowy obiekt kontenera jest niezdefiniowana.

- Jeśli kontener przechowuje obiekt funkcyjny *comp*, aby ustalić sposób uporządkowania kontrolowanej sekwencji i *comp* zgłaszającej wyjątek dowolnego rodzaju, stan wynikowy obiekt kontenera jest niezdefiniowana.

Klasy kontenera, zdefiniowane przez standardowej biblioteki języka C++ spełnić kilka dodatkowych wymagań, zgodnie z opisem w sekcjach.

Klasę szablonu pojemnika [listy](../standard-library/list-class.md) zapewnia zachowanie deterministyczne i są przydatne, nawet w obecności wyjątków opisanych powyżej. Na przykład jeśli wyjątek jest generowany podczas wstawiania jednego lub więcej elementów, kontener niezmieniony po lewej stronie, a wyjątek jest zgłaszany ponownie.

Dla *wszystkie* klasy kontenera definicją standardowej biblioteki języka C++, jeśli wyjątek zostanie zgłoszony podczas wywołania do następujących funkcji elementu członkowskiego, `insert`, `push_back`, lub `push_front`, kontener pozostanie niezmienione i wyjątek jest zgłaszany ponownie.

Aby uzyskać *wszystkich* klas kontenerów zdefiniowanych w standardowej biblioteki języka C++, jest zgłaszany żaden wyjątek podczas wywołania do następujących składowych: `pop_back`, `pop_front`.

Funkcja elementu członkowskiego [wymazać](../standard-library/container-class-erase.md) zgłasza wyjątek, tylko wtedy, gdy operacja kopiowania (przypisania lub kopiowania konstrukcja) zgłasza wyjątek.

Ponadto podczas kopiowania iterator, który został zwrócony przez funkcję elementu członkowskiego jest zgłaszany żaden wyjątek.

Funkcja elementu członkowskiego [wymiany](../standard-library/container-class-swap.md) sprawia, że dodatkowe obietnic dla *wszystkich* klasy kontenera definicją standardowej biblioteki języka C++:

- Funkcja elementu członkowskiego zgłasza wyjątek, tylko wtedy, gdy kontener przechowuje Al — obiekt programu przydzielania i `al` zgłasza wyjątek podczas kopiowania.

- Ważność odwołania, wskaźniki i Iteratory, które wyznaczają elementy kontrolowanej sekwencji, które są wymieniane.

Obiekt klasy kontenera, zdefiniowane przez standardowej biblioteki języka C++ przydziela i zwalnia pamięć dla sekwencję którą kontroluje, przez przechowywany obiekt typu `Alloc`, który zazwyczaj jest parametrem szablonu. Taki obiekt alokatora musi mieć ten sam interfejs zewnętrzny co obiekt klasy `allocator<Ty>`. W szczególności `Alloc` musi być taki sam typ co `Alloc::rebind<value_type>::other`

Aby uzyskać *wszystkich* klasy kontenera definicją standardowej biblioteki języka C++, funkcja elementu członkowskiego `Alloc get_allocator const;` zwraca kopię obiektu przechowywany obiekt alokatora. Należy zauważyć, że przechowywany obiekt alokatora *nie* kopiowany po przypisaniu obiektu kontenera. Wszystkie konstruktory inicjują wartość przechowywaną w `allocator`, `Alloc` Jeśli Konstruktor nie zawiera żadnego parametru alokatora.

Zgodnie ze standardem C++ klasy kontenera, zdefiniowane przez standardowej biblioteki języka C++ można założyć, że:

- Wszystkie obiekty klasy `Alloc` porównania równości.

- Typ `Alloc::const_pointer` jest taka sama jak `const Ty *`.

- Typ `Alloc::const_reference` jest taka sama jak `const Ty&`.

- Typ `Alloc::pointer` jest taka sama jak `Ty *`.

- Typ `Alloc::reference` jest taka sama jak `Ty&`.

W tej implementacji jednak kontenerów nie należy wprowadzać takie założenia. W związku z tym działają prawidłowo z obiektami alokatora, które są bardziej ambitne:

- Wszystkie obiekty klasy `Alloc` nie jest konieczne porównanie równego. (Obsługa wielu pul magazynu).

- Typ `Alloc::const_pointer` nie musi być taka sama jak `const Ty *`. (Wskaźnika elementu const może być klasą).

- Typ `Alloc::pointer` nie musi być taka sama jak `Ty *`. (Wskaźnik może mieć klasy).

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<przykładowy kontener >

## <a name="see-also"></a>Zobacz także

[\<Przykładowy kontener >](../standard-library/sample-container.md)<br/>
