---
title: Korzystanie z interfejsu IDispEventImpl (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: c532164788d359c7834759de01407d49c19463ca
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341479"
---
# <a name="using-idispeventimpl"></a>Korzystanie z interfejsu IDispEventImpl

Korzystając z `IDispEventImpl` do obsługi zdarzeń, konieczne będzie:

- Pochodzi z klasy [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Dodaj mapę ujścia zdarzeń do swojej klasy.

- Dodawanie wpisów do zdarzenia sink mapy za pomocą [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) lub [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) makra.

- Implementuje metody interesującego Cię w obsłudze.

- Powiadomienia i unadvise źródła zdarzeń.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób obsługi `DocumentChange` zdarzenia wywoływane przez programu Word **aplikacji** obiektu. To zdarzenie jest zdefiniowany jako metodę na `ApplicationEvents` dispinterface.

W przykładzie występuje z [przykładowe ATLEventHandling](../overview/visual-cpp-samples.md).

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

W przykładzie użyto `#import` ma generować pliki wymaganego nagłówka z biblioteki typów programu Word. Jeśli chcesz wykorzystać ten przykład z innymi wersjami programu Word, należy określić prawidłowe mso pliku dll. Na przykład pakiet Office 2000 zawiera mso9.dll i OfficeXP zapewnia mso.dll. Ten kod jest uproszczony w pliku stdafx.h:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

Poniższy kod zostanie wyświetlony w NotSoSimple.h. Odpowiedni kod jest oznaczone przez komentarzy:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Zobacz także

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)<br/>
[Przykładowe ATLEventHandling](../overview/visual-cpp-samples.md)
