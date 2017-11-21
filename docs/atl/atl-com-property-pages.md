---
title: "Strony właściwości COM ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: de062b5c9aedb064206dfc40f7c722a298ded774
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atl-com-property-pages"></a>Strony właściwości ALT COM
Strony właściwości COM udostępniają interfejs użytkownika do ustawiania właściwości (lub wywołanie metody) jeden lub więcej obiektów COM. Strony właściwości są często używane przez kontrolki ActiveX udostępnia interfejsy użytkownika sformatowanego, które umożliwiają właściwości formantu w czasie projektowania.  
  
 Strony właściwości są obiektów COM, które implementują [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) lub [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) interfejsu. Te interfejsy Podaj metod umożliwiających strony ma być skojarzone z `site` (obiekt COM reprezentuje kontener strony) i liczbę *obiektów* (obiektów COM metody, której zostanie wywołana w odpowiedzi na zmiany wprowadzone przez użytkownika na stronie właściwości). Kontener strony właściwości jest odpowiedzialny za wywołanie metod interfejsu strony właściwości mówić strony, gdy do wyświetlenia lub ukrycia interfejs użytkownika i kiedy należy zastosować zmiany wprowadzone przez użytkownika do obiektów.  
  
 Każdej strony właściwości mogą być tworzone całkowicie niezależnie od obiektów, którego właściwości można ustawić. Wszystkie te strony właściwości jest wymaga aby zrozumieć konkretnego interfejsu (lub zestawu interfejsów) i udostępniają interfejs użytkownika na potrzeby wywoływania metod, w tym interfejsie.  
  
 Aby uzyskać więcej informacji, zobacz [arkusze właściwości i strony właściwości](http://msdn.microsoft.com/library/windows/desktop/ms686577) w [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie strony właściwości](../atl/specifying-property-pages.md)  
 Zawiera listę kroków służącą do strony właściwości dla formantu zostanie i przedstawia przykład klasy.  
  
 [Implementacja strony właściwości](../atl/implementing-property-pages.md)  
 Zawiera listę kroków wdrażania strony właściwości, w tym metody do przesłonięcia. Przeprowadzi Cię przez pełny przykład oparte na ATLPages przykładowy program.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przykładowe ATLPages](../visual-cpp-samples.md)  
 Abstract próbki przykładowej ATLPages, która implementuje stronę właściwości przy użyciu `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Zawiera łącza do tematów koncepcyjne na temat programowania przy użyciu biblioteki Active Template Library.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

