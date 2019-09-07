---
title: Zdarzenia (C++/CX)
ms.date: 07/15/2019
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
ms.openlocfilehash: aab37353b1ea8d9f81a8e9a9ae489a4dd3542cc0
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740523"
---
# <a name="events-ccx"></a>Zdarzenia (C++/CX)

Typ środowisko wykonawcze systemu Windows może deklarować (czyli publikować) zdarzenia, a kod klienta w tym samym składniku lub w innych składnikach może subskrybować te zdarzenia, kojarząc *metody wywoływane z zdarzeniami* . Obsługa wielu zdarzeń może być skojarzona z pojedynczym zdarzeniem. Gdy obiekt publikacji zgłasza zdarzenie, spowoduje to wywołanie wszystkich programów obsługi zdarzeń. W ten sposób Klasa subskrybowania może wykonywać dowolną akcję niestandardową, gdy Wydawca zgłasza zdarzenie. Zdarzenie ma typ delegata, który określa sygnaturę, którą muszą dysponować wszystkie programy obsługi zdarzeń, aby subskrybować zdarzenie.

## <a name="consuming-events-in-windows-components"></a>Zużywanie zdarzeń w składnikach systemu Windows

Wiele składników w środowisko wykonawcze systemu Windows uwidacznia zdarzenia. Na przykład obiekt LightSensor wyzwala zdarzenie ReadingChanged, gdy czujnik zgłasza nową wartość luminescence. Gdy używasz obiektu LightSensor w programie, możesz zdefiniować metodę, która będzie wywoływana po wywołaniu zdarzenia ReadingChanged. Metoda może wykonać dowolną czynność do wykonania; jedyny wymóg polega na tym, że jego podpis musi być zgodny z podpisem obiektu delegowanego, który jest wywoływany. Aby uzyskać więcej informacji na temat sposobu tworzenia programu obsługi zdarzeń delegata i subskrybowania zdarzenia, zobacz [delegats](../cppcx/delegates-c-cx.md).

## <a name="creating-custom-events"></a>Tworzenie zdarzeń niestandardowych

### <a name="declaration"></a>Oświadczeń

Można zadeklarować zdarzenie w klasie ref lub interfejsie i może mieć publiczną, wewnętrzną (publiczną/prywatną), publiczną chronioną, chronioną, prywatną, chronioną lub prywatną dostępność. Podczas deklarowania zdarzenia wewnętrznie kompilator tworzy obiekt, który uwidacznia dwie metody dostępu: Dodaj i Usuń. Podczas subskrybowania obiektów procedury obsługi zdarzeń, obiekt zdarzenia przechowuje je w kolekcji. Gdy zdarzenie jest wyzwalane, obiekt zdarzenia wywołuje wszystkie programy obsługi na liście z kolei. Zdarzenie proste — podobnie jak w poniższym przykładzie — ma niejawny magazyn zapasowy, a także metody niejawnych `add` i `remove` metod dostępu. Można również określić własne metody dostępu w taki sam sposób, w jaki można określić niestandardowe `get` i `set` metody dostępu dla właściwości.  Klasa implementująca nie może ręcznie przechodzić przez listę subskrybentów zdarzeń w zdarzeniu prostym.

Poniższy przykład pokazuje sposób deklarowania i wyzwalania zdarzenia. Zwróć uwagę, że zdarzenie ma typ delegata i jest zadeklarowana przy użyciu symbolu "^".

[!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]

### <a name="usage"></a>Użycie

Poniższy przykład przedstawia sposób, w jaki Klasa subskrybowania `+=` używa operatora do subskrybowania zdarzenia i zapewnia procedurę obsługi zdarzeń do wywołania, gdy zdarzenie jest wyzwalane. Zwróć uwagę, że podana funkcja jest zgodna z sygnaturą delegata zdefiniowanego po stronie wydawcy w `EventTest` przestrzeni nazw.

[!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]

> [!WARNING]
> Ogólnie rzecz biorąc, lepiej jest użyć nazwanej funkcji zamiast wyrażenia lambda, w przypadku obsługi zdarzeń, chyba że nie trzeba uważać, aby uniknąć cyklicznych odwołań. Nazwana funkcja przechwytuje wskaźnik "This" przez słabe odwołanie, natomiast wyrażenie lambda przechwytuje je przez silną referencję i tworzy odwołanie cykliczne. Aby uzyskać więcej informacji, zobacz [słabe odwołania i cykleC++przerywania (/CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

### <a name="custom-add-and-remove-methods"></a>Niestandardowe metody dodawania i usuwania

Wewnętrznie, zdarzenie ma metodę Add, metoda Remove i metodę podniesienia. Gdy kod klienta subskrybuje zdarzenie, wywoływana jest metoda Add i delegat, który jest przesyłany, jest dodawany do listy wywołań zdarzenia. Klasa publikacji wywołuje zdarzenie, powoduje wywołanie metody Invoke (), a każdy delegat na liście jest wywoływany z kolei. Subskrybent może usunąć siebie z listy delegatów, co powoduje wywołanie metody usuwania zdarzenia. Kompilator dostarcza domyślne wersje tych metod, jeśli nie są zdefiniowane w kodzie; są one znane jako zdarzenia uproszczone. W wielu przypadkach jest to wymagane przez proste zdarzenie.

Możesz określić niestandardowe metody dodawania, usuwania i wywoływania dla zdarzenia, jeśli konieczne jest wykonanie logiki niestandardowej w odpowiedzi na dodawanie lub usuwanie subskrybentów. Na przykład jeśli masz kosztownego obiektu, który jest wymagany tylko w przypadku raportowania zdarzeń, możesz opóźnieniemć Tworzenie obiektu do momentu, gdy klient rzeczywiście zasubskrybuje zdarzenie.

W następnym przykładzie pokazano, jak dodać niestandardowe metody dodawania, usuwania i wywoływania do zdarzenia:

[!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]

## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Usuwanie procedury obsługi zdarzeń z boku subskrybenta

W niektórych rzadkich przypadkach może być konieczne usunięcie programu obsługi zdarzeń dla zdarzenia, które zostało wcześniej zasubskrybowane. Na przykład możesz chcieć zastąpić go innym programem obsługi zdarzeń lub usunąć niektóre zasoby, które są przez niego przechowywane. Aby usunąć program obsługi, należy zapisać EventRegistrationToken, który jest zwracany z `+=` operacji. Można następnie użyć `-=` operatora na tokenie, aby usunąć procedurę obsługi zdarzeń.  Jednak pierwotna procedura obsługi nadal może być wywoływana nawet po jej usunięciu. W związku z tym, jeśli zamierzasz usunąć program obsługi zdarzeń, Utwórz flagę elementu członkowskiego i ustaw ją, jeśli zdarzenie zostanie usunięte, a następnie w programie obsługi zdarzeń Sprawdź flagę i wróć natychmiast, jeśli jest ustawiona. W następnym przykładzie pokazano wzorzec podstawowy.

[!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]

### <a name="remarks"></a>Uwagi

Wiele programów obsługi może być skojarzonych z tym samym zdarzeniem. Źródło zdarzenia sekwencyjnie wywołuje wszystkie procedury obsługi zdarzeń z tego samego wątku. Jeśli odbiornik zdarzeń jest blokowany w ramach metody obsługi zdarzeń, blokuje Źródło zdarzenia wywołującego inne procedury obsługi zdarzeń dla tego zdarzenia.

Kolejność, w której źródło zdarzeń wywołuje procedury obsługi zdarzeń dla odbiorców zdarzeń, nie jest gwarantowana i może się różnić od wywołania wywołania.

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Delegaty](../cppcx/delegates-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
