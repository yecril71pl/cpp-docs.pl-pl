---
title: Zdarzenia (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98231f0803270a9e033529e163ff2cc23cdd64e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089641"
---
# <a name="events-ccx"></a>Zdarzenia (C + +/ CX)
Windows obsługi można zadeklarować typu (publikowanie) zdarzenia i kod klienta w tej samej składnika lub inne składniki mogą subskrybować te zdarzenia, kojarząc metody wywołane *procedury obsługi zdarzeń* ze zdarzeniem. Wielu obsług zdarzeń może być skojarzony z pojedynczego zdarzenia. Podczas publikowania obiektu zgłasza zdarzenie, powoduje wszystkich procedur obsługi zdarzeń do wywołania. W ten sposób subskrybującego klasy mogą wykonywać, niezależnie od akcji niestandardowej jest odpowiednia, gdy wydawca wywołuje zdarzenie. Zdarzenie ma typ delegata, który określa podpis musi mieć wszystkie procedury obsługi zdarzeń, aby subskrybować zdarzenia.  
  
## <a name="consuming-events-in-windows-components"></a>Wykorzystywanie zdarzeń składników systemu Windows  
 Wiele składników w środowisku wykonawczym systemu Windows ujawnia zdarzenia. Na przykład obiekt LightSensor generowane zdarzenie ReadingChanged, gdy czujnik zgłasza nową wartość jaskrawość. Korzystając z obiektu LightSensor w programie, można zdefiniować metody, która będzie wywoływana po uruchomieniu zdarzenia ReadingChanged. Metoda można wykonać dowolne wykonania; Jedynym wymaganiem jest, że podpis musi odpowiadać podpisu delegata, który jest, aby uzyskać więcej informacji o sposobie tworzenia obiektu delegowanego obsługi zdarzeń i subskrybowanie zdarzeń, zobacz [delegatów](../cppcx/delegates-c-cx.md).  
  
## <a name="creating-custom-events"></a>Tworzenie zdarzeń niestandardowych  
  
### <a name="declaration"></a>Deklaracja  
 Można zadeklarować zdarzenia w klasie ref lub interfejs i może być publiczne, wewnętrzne (publiczny/prywatny), publicznego chroniony, chroniony, prywatne chronione lub prywatnej ułatwień dostępu. Deklaracja zdarzenia wewnętrznie kompilator tworzy obiekt, który udostępnia dwie metody dostępu: Dodawanie i usuwanie. Jeśli obiekty subskrybującego Zarejestruj procedury obsługi zdarzeń, obiekt zdarzenia przechowuje je w kolekcji. Gdy zdarzenie jest wywoływane, obiekt zdarzenia z kolei wywołuje wszystkich programów obsługi na liście. Prosta zdarzeń — takich jak w poniższym przykładzie — ma również jako niejawne magazynu zapasowego niejawne `add` i `remove` metody dostępu. Można również określić własne akcesorów w taki sam sposób, że można określić niestandardowe `get` i `set` metody dostępu właściwości.  Klasy implementującej nie można ręcznie przełączać się między listy subskrybenta zdarzeń w przypadku prostych.  
  
 Poniższy przykład pokazuje, jak można zadeklarować i zdarzenia. Powiadomienie, że zdarzenie ma typ delegata i jest zadeklarowany za pomocą "^" symbolu.  
  
 [!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]  
  
### <a name="usage"></a>Użycie  
 W poniższym przykładzie pokazano, jak używa klasy subskrybującego `+=` operatora, aby subskrybować zdarzenia i podać program obsługi zdarzeń do wywołania, gdy zdarzenie jest wywoływane. Zwróć uwagę, czy funkcji, który został dostarczony zgodny podpisu delegata, która jest zdefiniowana na stronie wydawcy w `EventTest` przestrzeni nazw.  
  
 [!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]  
  
> [!WARNING]
>  Ogólnie rzecz biorąc lepiej jest do użycia dla programu obsługi zdarzeń funkcji o nazwie zamiast lambda, chyba że zostanie zastosowane szczególną uwagę, aby uniknąć odwołania cykliczne. Funkcji o nazwie przechwytuje wskaźnik "this" przez odwołanie słabe lambda przechwytuje go przez silne odwołanie i tworzy odwołanie cykliczne. Aby uzyskać więcej informacji, zobacz [słabe odwołania i cykle podziału (C + +/ CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).  
  
### <a name="custom-add-and-remove-methods"></a>Niestandardowe Dodawanie i usuwanie metody  
 Wewnętrznie zdarzenie ma metodę add, metoda usuwania i metody wzrostu. Gdy kod klienta subskrybuje zdarzenia, jest wywoływana metoda add a delegata, który jest przekazywany w zostanie dodany do listy wywołania zdarzenia. Klasa publikowania wywołuje zdarzenie, powoduje wywoływanej metody raise() i każdego delegata na liście jest wywoływany z kolei. Subskrybent można usunąć się na liście delegata, co powoduje, że metoda usuwania zdarzenia do wywołania. Kompilator zapewnia domyślnej wersji tych metod, jeśli nie należy je zdefiniować w kodzie; te są nazywane trivial zdarzenia. W wielu przypadkach trivial zdarzenie jest wszystkie, która jest wymagana.  
  
 Można określić niestandardowe dodawania, usuwania i wywoływania na zdarzenie jeśli zajdzie potrzeba wykonania niestandardowej logiki w odpowiedzi na dodawanie i usuwanie subskrybentów. Na przykład, jeśli masz kosztowne obiektu, który jest wymagany do raportowania zdarzeń, tylko wtedy, w przypadku można opóźnieniem opóźnienia tworzenia obiektu aż do zdarzenia faktycznie zasubskrybowaniem przez klienta.  
  
 W kolejnym przykładzie pokazano, jak dodać niestandardowe dodawania, usuwania i wywoływania na zdarzenie:  
  
 [!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]  
  
## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Usuwanie ze strony subskrybenta program obsługi zdarzeń  
 W rzadkich przypadkach możesz usunąć program obsługi zdarzeń dla zdarzenia, które wcześniej subskrybujesz. Na przykład chcesz zastąpić innego programu obsługi zdarzeń lub chcesz usunąć niektóre zasoby, które są przechowywane przez nią. Aby usunąć program obsługi, należy zapisać EventRegistrationToken, która jest zwracana z `+=` operacji. Następnie można użyć `-=` operatora w tokenie, aby usunąć program obsługi zdarzeń.  Oryginalny obsługi można jednak nadal wywoływane nawet po jego usunięciu. W związku z tym jeśli zamierzasz usunąć program obsługi zdarzeń, Utwórz flagę elementu członkowskiego i ustaw ją, jeśli zdarzenie zostanie usunięty, a następnie zdarzeń programu obsługi, sprawdź flagi i zwracać natychmiast, jeśli jest ustawiona. W kolejnym przykładzie pokazano podstawowy wzorzec.  
  
 [!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]  
  
### <a name="remarks"></a>Uwagi  
 Procedury obsługi wielu może być skojarzony z tego samego zdarzenia. Źródło zdarzenia po kolei wywołuje do wszystkich procedur obsługi zdarzeń z tego samego wątku. Jeśli odbiorca zdarzenia blokuje w metoda obsługi zdarzeń, blokuje źródło zdarzenia z wywołaniem innych programów obsługi zdarzeń dla tego zdarzenia.  
  
 Kolejność, w którym źródło zdarzenia wywołuje programów obsługi zdarzeń na odbiorcy zdarzeń nie jest gwarantowana i może różnić się od wywołaniami.  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Obiekty delegowane](../cppcx/delegates-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)