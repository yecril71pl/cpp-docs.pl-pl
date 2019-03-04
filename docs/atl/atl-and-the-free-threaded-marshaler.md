---
title: ATL i marshaler trybu wolnych wątków
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: ddea5a74dbd40d097398d04c0b2bc274df5ec972
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300001"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL i marshaler trybu wolnych wątków

Strona atrybutów ATL prostego obiektu kreatora zawiera opcję umożliwiającą klasy agregacji marshaler trybu (programu FTM).

Kreator generuje kod, aby utworzyć wystąpienie marshaler trybu w `FinalConstruct` i wersji tego wystąpienia w `FinalRelease`. Makra COM_INTERFACE_ENTRY_AGGREGATE jest automatycznie dodawana do mapy COM, aby upewnić się, że `QueryInterface` żądań dla [IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal) są obsługiwane przez marshaler trybu.

Marshaler trybu umożliwia bezpośredni dostęp do interfejsów na obiekcie z żadnym z wątków w tym samym procesie przyspieszenia apartamentu dla wielu wywołań. Ta opcja jest przeznaczona dla klas, które używają obu modelu wątkowości.

Przy użyciu tej opcji, klasy musi ponosi odpowiedzialność za bezpieczeństwo wątków ich danych. Ponadto obiekty, które agregacji marshaler trybu i muszą korzystać wskaźniki interfejsu uzyskane z innych obiektów, należy wykonać dodatkowe kroki, aby upewnić się, że interfejsy są organizowane poprawnie. Obejmuje to zwykle przechowywania wskaźniki interfejsu w tabeli interfejsu globalnego (GIT) i pobieranie wskaźnika z GIT każdorazowo, gdy jest używany. ATL dostarcza klasę [CComGITPtr](../atl/reference/ccomgitptr-class.md) przydatne podczas używania wskaźniki interfejsu, przechowywane w usłudze GIT.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/desktop/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Kiedy używać tabeli interfejsu globalnego](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[Problemy wielowątkowości dotyczące serwera przetwarzania](/windows/desktop/com/in-process-server-threading-issues)
