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
ms.openlocfilehash: 94e4961c69e9441d160d72d9b72afcee3677e25f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491909"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL i marshaler trybu wolnych wątków

Strona atrybutów Kreatora prostych obiektów ATL zawiera opcję umożliwiającą klasie agregowanie organizatora trybu wolnych wątków (FTM).

Kreator generuje kod, aby utworzyć wystąpienie elementu Marshal of Free threader w `FinalConstruct` i wydać to wystąpienie w. `FinalRelease` Makro COM_INTERFACE_ENTRY_AGGREGATE jest automatycznie dodawane do mapy com, aby upewnić się `QueryInterface` , że żądania [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal) są obsługiwane przez organizatora trybu wolnych wątków.

Organizator wolnych wątków umożliwia bezpośredni dostęp do interfejsów w obiekcie z dowolnego wątku w tym samym procesie, przyspieszając wywołania między różnymi komórkami. Ta opcja jest przeznaczona dla klas, które używają obu modeli wątkowości.

W przypadku korzystania z tej opcji klasy muszą być odpowiedzialne za bezpieczeństwo wątków swoich danych. Ponadto obiekty, które agregują organizatora wolnych wątków i muszą używać wskaźników interfejsu uzyskanych z innych obiektów, muszą podejmować dodatkowe kroki, aby upewnić się, że interfejsy są prawidłowo organizowane. Zazwyczaj obejmuje to przechowywanie wskaźników interfejsu w globalnej tabeli interfejsu (GIT) i uzyskiwanie wskaźnika z narzędzia GIT za każdym razem, gdy jest używany. ATL zawiera klasy [CComGITPtr](../atl/reference/ccomgitptr-class.md) , które ułatwiają korzystanie ze wskaźników interfejsu przechowywanych w usłudze git.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Kiedy używać globalnej tabeli interfejsów](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Problemy wątkowości serwera w procesie](/windows/win32/com/in-process-server-threading-issues)
