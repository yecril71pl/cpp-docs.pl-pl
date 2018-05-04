---
title: ATL i Marshaler trybu wolnych wątków | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1716985adf65b714a418f20d3873f45c32d368b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL i marshaler trybu wolnych wątków
Strona atrybutów ATL prosty obiekt kreatora zawiera opcję umożliwiającą klasy agregacji Organizator trybu wolnych wątków (FTM).  
  
 Kreator generuje kod w celu utworzenia wystąpienia Organizator trybu wolnych wątków w `FinalConstruct` i wersji tego wystąpienia w `FinalRelease`. A `COM_INTERFACE_ENTRY_AGGREGATE` makro jest automatycznie dodawany do mapy COM, aby upewnić się, że `QueryInterface` żądań dotyczących [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707) są obsługiwane przez Organizator trybu wolnych wątków.  
  
 Organizator trybu wolnych wątków umożliwia bezpośredni dostęp do interfejsów na obiekt z dowolnego wątku, w tym samym procesie przyspieszania wywołań między apartamentu. Ta opcja jest przeznaczona dla klas, które używają obu modelu wątkowości.  
  
 Korzystając z tej opcji, klasy, należy wykonać odpowiedzialność za bezpieczeństwo wątków ich danych. Ponadto obiekty agregacji Organizator trybu wolnych wątków, które muszą używać wskaźniki interfejsu uzyskane z innych obiektów muszą wykonać dodatkowe czynności, aby upewnić się, że interfejsy są poprawnie przekazywane. Obejmuje to zwykle przechowywania wskaźniki interfejsu w tabeli interfejsu globalnego (GIT) i uzyskiwanie wskaźnika z GIT każdym razem, gdy jest używany. ATL zawiera klasę [CComGITPtr](../atl/reference/ccomgitptr-class.md) ułatwiają wskaźniki interfejsu przechowywane w usłudze GIT.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [Kiedy należy używać Tabela interfejsu globalnego](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Problemy wielowątkowości Server wewnątrzprocesowe](http://msdn.microsoft.com/library/windows/desktop/ms687205)

