---
title: "Określanie strony właściwości (ALT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ISpecifyPropertyPages
dev_langs: C++
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a4519bee0d1f9c5e433114f12a6568bde6b8c4fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-property-pages"></a>Określanie strony właściwości
Podczas tworzenia formantu ActiveX, często można skojarzyć go z strony właściwości, które mogą służyć do ustawiania właściwości formantu. Kontroluje użycia kontenery **ISpecifyPropertyPages** interfejsu, aby dowiedzieć się, które strony właściwości może służyć do ustawiania właściwości formantu. Musisz zaimplementować ten interfejs formantu.  
  
 Aby zaimplementować **ISpecifyPropertyPages** za pomocą biblioteki ATL, wykonaj następujące czynności:  
  
1.  Pochodzi z klasy [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).  
  
2.  Dodaj wpis dla **ISpecifyPropertyPages** do własnej klasy COM mapy.  
  
3.  Dodaj [PROP_PAGE](reference/property-map-macros.md#prop_page) wpisu mapę właściwości dla każdej strony skojarzone z formantu.  
  
> [!NOTE]
>  Podczas generowania za pomocą formantu standardowego [Kreator formantu ATL](../atl/reference/atl-control-wizard.md), będzie miał tylko do dodawania `PROP_PAGE` wpisów do mapy właściwości. Kreator generuje kod wymagane inne czynności.  
  
 Kontenerów dobrze działające będą wyświetlane na stronach właściwości określony w tej samej kolejności jak `PROP_PAGE` wpisy mapy właściwości. Ogólnie rzecz biorąc należy umieścić wpisów stron właściwości standardowych po pozycji niestandardowych stron w mapie właściwości, aby użytkownicy widzieli najpierw stron specyficzne dla formantu.  
  
## <a name="example"></a>Przykład  
 Następujące klasy kalendarza kontrolować używa **ISpecifyPropertyPages** interfejsu mówić kontenerów, które właściwości można ustawić za pomocą strony niestandardowa data i strony kolorów podstawowych.  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../atl/atl-com-property-pages.md)   
 [Przykładowe ATLPages](../visual-cpp-samples.md)

