---
title: Strony właściwości COM ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fdf0d53cca00424c2c933e2578fb5c70b7d07e1
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465047"
---
# <a name="atl-com-property-pages"></a>Strony właściwości ALT COM
Strony właściwości COM udostępniają interfejs użytkownika do ustawiania właściwości (lub wywoływania metod) jeden lub więcej obiektów COM. Strony właściwości są często używane przez formanty ActiveX zapewniające bogatych interfejsów użytkownika umożliwiające właściwości formantu należy ustawić w czasie projektowania.  
  
 Strony właściwości są obiektów COM, które implementują [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) lub [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) interfejsu. Te interfejsy, zapewniają metody, które umożliwiają strony do skojarzenia z `site` (obiekt COM reprezentujący kontener strony) i liczbę *obiektów* (obiekty COM metod, których zostanie wywołana w odpowiedzi na zmiany wprowadzone przez użytkownika na stronie właściwości). Kontener strony właściwości jest odpowiedzialny za wywoływanie metod na interfejsie strony właściwości sprawdzić na stronie, gdy pokazać lub ukryć jego interfejs użytkownika i kiedy należy zastosować zmiany wprowadzone przez użytkownika do obiektów.  
  
 Każdą stronę właściwości mogą być wbudowane w całkowicie niezależnie od obiektów, których właściwości można ustawić. Wszystko to strona właściwości jest wymaga, aby zrozumieć określonego interfejsu (lub zestawu interfejsów) i udostępniają interfejs użytkownika na potrzeby wywoływania metod, w tym interfejsie.  
  
 Aby uzyskać więcej informacji, zobacz [arkusze właściwości i strony właściwości](http://msdn.microsoft.com/library/windows/desktop/ms686577) w zestawie Windows SDK.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie stron właściwości](../atl/specifying-property-pages.md)  
 Lista czynności prowadzących do określanie stron właściwości dla sterować i przedstawia przykład klasy.  
  
 [Implementowanie stron właściwości](../atl/implementing-property-pages.md)  
 Lista czynności prowadzących do Implementowanie stron właściwości, włączając w to metody do przesłonięcia. Przeprowadzi Cię przez kompletny przykład, w oparciu o ATLPages przykładowy program.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przykładowe ATLPages](../visual-cpp-samples.md)  
 Abstrakcyjny próbki dla przykładu ATLPages, która implementuje stronę właściwości przy użyciu `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Zawiera łącza do tematów pojęciowych dotyczące programowania przy użyciu biblioteki Active Template Library.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

