---
title: Zdarzenia (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f45e85b552625fb7975612d0d307709cc2b7426
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109074"
---
# <a name="events-ccx"></a>Zdarzenia (C + +/ CX)

Windows obsługi można zadeklarować typu (publikowanie) zdarzenia i kod klienta w jednym składniku lub inne składniki mogą subskrybować te zdarzenia, kojarząc metody o nazwie *procedury obsługi zdarzeń* ze zdarzeniem. Wiele procedur obsługi zdarzeń może być skojarzony z pojedynczego zdarzenia. Podczas publikowania obiektu wywołuje zdarzenie, powoduje wszystkich procedur obsługi zdarzeń do wywołania. W ten sposób subskrybującą klasy można wykonać dowolną akcję niestandardową jest odpowiednie w przypadku, gdy wydawca wywołuje zdarzenie. Zdarzenie ma typ delegata, który określa podpis wszystkich procedur obsługi zdarzeń musi mieć, aby subskrybować zdarzenia.

## <a name="consuming-events-in-windows-components"></a>Używanie zdarzeń w składnikach Windows

Wiele składników środowiska wykonawczego Windows uwidocznić zdarzenia. Na przykład obiekt LightSensor wyzwala zdarzenie ReadingChanged, gdy czujnik zgłasza nową wartość jaskrawość. Korzystając z obiektu LightSensor w swoim programie, można zdefiniować metodę, która zostanie wywołana, gdy jest wyzwalane zdarzenie ReadingChanged. Metoda można wykonać dowolne mu; Jedynym wymaganiem jest, że jeho signatura musi odpowiadać podpisowi delegata, który jest, aby uzyskać więcej informacji o sposobie tworzenia delegata obsługi zdarzeń i subskrybować zdarzenie, zobacz [delegatów](../cppcx/delegates-c-cx.md).

## <a name="creating-custom-events"></a>Tworzenie zdarzeń niestandardowych

### <a name="declaration"></a>Deklaracja

Można zadeklarować zdarzenia w klasie ref lub interfejs i może mieć publiczne, wewnętrzne (publiczny/prywatny), chronione publiczne, chronione, prywatne protected lub private ułatwień dostępu. Kiedy Deklarujesz zdarzenie, wewnętrznie kompilator tworzy obiekt, który udostępnia dwie metody dostępu: Dodawanie i usuwanie. Jeśli obiekty subskrybującą Zarejestruj procedury obsługi zdarzeń, z obiektem zdarzenia przechowuje je w kolekcji. Gdy zdarzenie jest wyzwalane, z obiektem zdarzenia z kolei wywołuje całej obsługi na liście. Prosta zdarzeń — takich jak w poniższym przykładzie — ma magazyn zapasowy niejawne również jako niejawne `add` i `remove` metody dostępu. Można również określić własne metody dostępu, w taki sam sposób, że można określić niestandardowe `get` i `set` metod dostępu właściwości.  Klasy implementującej ręcznie nie może przechodzić przez listę subskrybentów zdarzeń w zdarzeniu prosta.

Poniższy przykład pokazuje, jak zadeklarować i wywołać zdarzenie. Zwróć uwagę, że zdarzenie jest typem delegowanym i jest zadeklarowana za pomocą "^" symboli.

[!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]

### <a name="usage"></a>Użycie

W poniższym przykładzie pokazano, jak korzysta z klasy subskrybującą `+=` operator subskrybować zdarzenia w celu zapewnienia obsługi zdarzeń do wywołania, gdy zdarzenie jest uruchamiane. Należy zauważyć, że funkcja, która znajduje się pasuje do podpisu delegata, która jest zdefiniowana na stronie wydawcy w `EventTest` przestrzeni nazw.

[!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]

> [!WARNING]
> Ogólnie rzecz biorąc lepiej jest do użytku o nazwie funkcji, zamiast wyrażenia lambda, program obsługi zdarzeń, chyba że Zwróć szczególną uwagę aby uniknąć odwołania cykliczne. Funkcja o nazwie przechwytuje wskaźnik "this" przez słabe odwołanie, wyrażenie lambda przechwytuje go przez silne odwołanie i tworzy odwołanie cykliczne. Aby uzyskać więcej informacji, zobacz [słabe odwołania i przerywanie cykli (C + +/ CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

### <a name="custom-add-and-remove-methods"></a>Niestandardowe Dodawanie i usuwanie form

Wewnętrznie zdarzenie ma metodę add, metoda usuwania i metody wzrostu. Gdy kod klienta subskrybuje zdarzenie, wywoływana jest metoda add a delegata, który jest przekazywany jest dodawany do listy wywołań zdarzeń. Publikowanie klasa wywołuje zdarzenie, sprawia, że wywoływanej metody raise() i każdego delegata na liście jest wywoływana z kolei. Subskrybent usunięciem się z listy delegata, co powoduje, że metoda usuwania zdarzeń do wywołania. Kompilator zapewnia domyślne wersje tych metod, jeżeli nie zdefiniujesz je w kodzie; są to znane jako proste zdarzenia. W wielu przypadkach trivial zdarzeń to wszystkie, które są wymagane.

Można określić niestandardowe dodawania, usuwania i wywoływanie metody dla zdarzenia, jeśli zajdzie potrzeba wykonania niestandardowej logiki w odpowiedzi na dodawanie i usuwanie subskrybentów. Na przykład, jeśli masz kosztowne obiekt, który jest tylko wymagane dla raportowania zdarzeń, użytkownik może opóźnieniem odroczyć Tworzenie obiektu do momentu klient rzeczywiście subskrybuje zdarzenie.

W kolejnym przykładzie pokazano, jak dodać niestandardowe dodawania, usuwania i wywoływanie metod na zdarzenie:

[!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]

## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Usuwanie programu obsługi zdarzeń z boku subskrybenta

W rzadkich przypadkach warto usunąć program obsługi zdarzeń dla zdarzenia, które wcześniej subskrybowanego przez Ciebie. Na przykład możesz chcieć zastąpić innego programu obsługi zdarzeń lub możesz chcieć usunąć niektóre zasoby, które są przechowywane przez nią. Aby usunąć program obsługi, należy zapisać EventRegistrationToken, który jest zwracany z `+=` operacji. Następnie można użyć `-=` operator na tokenie Aby usunąć program obsługi zdarzeń.  Oryginalny program obsługi może jednak nadal wywoływane nawet w przypadku, po jego usunięciu. W związku z tym jeśli zamierzasz usunąć program obsługi zdarzeń, utworzyć flagę elementu członkowskiego i ustaw ją, jeśli zdarzenie zostanie usunięty, a następnie w zdarzeniu programu obsługi, sprawdź flagi i natychmiast zwróci, jeśli jest ustawiony. Następny przykład przedstawia podstawowy wzorzec.

[!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]

### <a name="remarks"></a>Uwagi

Procedury obsługi wielu może być skojarzony z tego samego zdarzenia. Źródło zdarzenia wywoła po kolei wszystkich procedur obsługi zdarzeń z tym samym wątku. Jeśli odbiorca zdarzenia blokuje w obrębie metody obsługi zdarzeń, blokuje źródła zdarzeń z wywołaniem inne procedury obsługi zdarzeń dla tego zdarzenia.

Kolejność, w którym źródło zdarzeń wywołuje procedury obsługi zdarzeń w odbiorcy zdarzeń nie ma żadnej gwarancji i mogą się różnić z wywołaniami.

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Delegaci](../cppcx/delegates-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)