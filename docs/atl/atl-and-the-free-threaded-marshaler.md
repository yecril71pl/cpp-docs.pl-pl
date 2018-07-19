---
title: ATL i Marshaler trybu wolnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 015b07e5870aa6269dc76af8610d42fb469a6d33
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848353"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL i marshaler trybu wolnych wątków
Strona atrybutów ATL prostego obiektu kreatora zawiera opcję umożliwiającą klasy agregacji marshaler trybu (programu FTM).  
  
 Kreator generuje kod, aby utworzyć wystąpienie marshaler trybu w `FinalConstruct` i wersji tego wystąpienia w `FinalRelease`. Makra COM_INTERFACE_ENTRY_AGGREGATE jest automatycznie dodawana do mapy COM, aby upewnić się, że `QueryInterface` żądań dla [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707) są obsługiwane przez marshaler trybu.  
  
 Marshaler trybu umożliwia bezpośredni dostęp do interfejsów na obiekcie z żadnym z wątków w tym samym procesie przyspieszenia apartamentu dla wielu wywołań. Ta opcja jest przeznaczona dla klas, które używają obu modelu wątkowości.  
  
 Przy użyciu tej opcji, klasy musi ponosi odpowiedzialność za bezpieczeństwo wątków ich danych. Ponadto obiekty, które agregacji marshaler trybu i muszą korzystać wskaźniki interfejsu uzyskane z innych obiektów, należy wykonać dodatkowe kroki, aby upewnić się, że interfejsy są organizowane poprawnie. Obejmuje to zwykle przechowywania wskaźniki interfejsu w tabeli interfejsu globalnego (GIT) i pobieranie wskaźnika z GIT każdorazowo, gdy jest używany. ATL dostarcza klasę [CComGITPtr](../atl/reference/ccomgitptr-class.md) przydatne podczas używania wskaźniki interfejsu, przechowywane w usłudze GIT.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [Kiedy używać tabeli interfejsu globalnego](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Problemy wielowątkowości dotyczące serwera przetwarzania](http://msdn.microsoft.com/library/windows/desktop/ms687205)

