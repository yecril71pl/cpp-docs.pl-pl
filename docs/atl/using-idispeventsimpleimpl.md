---
title: Korzystanie z interfejsu IDispEventSimpleImpl (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00dadde438af1b4de820316dd4dc50e773827aca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107528"
---
# <a name="using-idispeventsimpleimpl"></a>Korzystanie z interfejsu IDispEventSimpleImpl

Korzystając z `IDispEventSimpleImpl` do obsługi zdarzeń, konieczne będzie:

- Pochodzi z klasy [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).

- Dodaj mapę ujścia zdarzeń do swojej klasy.

- Zdefiniuj [_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) struktury zawierająca opis zdarzenia.

- Dodawanie wpisów do zdarzenia sink mapy za pomocą [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) makra.

- Implementuje metody interesującego Cię w obsłudze.

- Powiadomienia i unadvise źródła zdarzeń.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób obsługi `DocumentChange` zdarzenia wywoływane przez programu Word **aplikacji** obiektu. To zdarzenie jest zdefiniowany jako metodę na `ApplicationEvents` dispinterface.

W przykładzie występuje z [przykładowe ATLEventHandling](../visual-cpp-samples.md).  

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

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

Wszystkie informacje z biblioteki typów, które faktycznie używana w tym przykładzie jest identyfikator CLSID słowa `Application` obiektu i identyfikatorem IID `ApplicationEvents` interfejsu. Te informacje tylko jest używany w czasie kompilacji.

Poniższy kod zostanie wyświetlony w Simple.h. Odpowiedni kod jest oznaczone przez komentarzy:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

Poniższy kod jest Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)<br/>
[Przykładowe ATLEventHandling](../visual-cpp-samples.md)

