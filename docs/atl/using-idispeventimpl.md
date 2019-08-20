---
title: Korzystanie z IDispEventImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: 9684781ba99d96e2c58d450ee0ff892374e33aef
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630598"
---
# <a name="using-idispeventimpl"></a>Korzystanie z interfejsu IDispEventImpl

W przypadku `IDispEventImpl` korzystania z programu do obsługi zdarzeń należy:

- Utwórz klasę z [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Dodaj mapę ujścia zdarzeń do swojej klasy.

- Dodaj wpisy do mapy ujścia zdarzeń przy użyciu makra [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) lub [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) .

- Zaimplementuj metody, które chcesz obsłużyć.

- Doradzanie i dedoradzanie źródła zdarzeń.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `DocumentChange` jak obsłużyć zdarzenie wywoływane przez obiekt **aplikacji** programu Word. To zdarzenie jest definiowane jako metoda w `ApplicationEvents` dispinterface.

Przykład pochodzi z [próbki ATLEventHandling](../overview/visual-cpp-samples.md).

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

Ten przykład używa `#import` do generowania wymaganych plików nagłówkowych z biblioteki typów programu Word. Jeśli chcesz użyć tego przykładu z innymi wersjami programu Word, musisz określić właściwy plik DLL Mso. Na przykład pakiet Office 2000 zapewnia Mso9. dll, a OfficeXP. dll. Ten kod jest uproszczony z *PCH. h* (*stdafx. h* w Visual Studio 2017 i starszych):

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

Poniższy kod pojawia się w NotSoSimple. h. Odpowiedni kod jest zanotowany przez Komentarze:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Zobacz także

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)<br/>
[Przykład ATLEventHandling](../overview/visual-cpp-samples.md)
