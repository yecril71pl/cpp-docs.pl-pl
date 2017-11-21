---
title: Ograniczenia funkcji CImage w starszych systemach operacyjnych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CImage
dev_langs: C++
helpviewer_keywords: CImage class [MFC], limitations
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb13e31df1b30c775d1e961f09b10163d06b1ea7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cimage-limitations-with-earlier-operating-systems"></a>Ograniczenia funkcji CImage w przypadku starszych systemów operacyjnych
Wiele `CImage` funkcje działają tylko z nowszymi wersjami systemu Windows: Windows 95/98 lub Windows NT 4.0 ani Windows 2000. W tym artykule opisano ograniczenia wersji niektórych metod.  
  
 [CImage::PlgBlt](../atl-mfc-shared/reference/cimage-class.md#plgblt) i [CImage::MaskBlt](../atl-mfc-shared/reference/cimage-class.md#maskblt) współpracują tylko systemu Windows NT 4.0 lub nowszy. Nie będzie działać na aplikacje działające w systemie Windows 95/98 lub nowszym.  
  
 [CImage::AlphaBlend](../atl-mfc-shared/reference/cimage-class.md#alphablend) i [CImage::TransparentBlt](../atl-mfc-shared/reference/cimage-class.md#transparentblt) współpracują tylko systemu Windows 2000 lub nowszego i systemu Windows 98 lub nowszego, ponieważ należy połączyć z msimg32.lib do użycia tych metod. (Ta biblioteka jest dostępne tylko dla aplikacji z systemem Windows 2000 lub nowszym i Windows 98 lub nowszego).  
  
 Można uwzględnić `AlphaBlend` i `TransparentBlt` w aplikacji, która działa w systemie Windows 95 lub Windows NT 4.0 tylko wtedy, gdy te metody nigdy nie jest wywoływana. Jeśli aplikacja zawiera tych metod, a musi być uruchomione w starszych systemach operacyjnych, należy użyć konsolidatora [/delayload](../build/reference/delayload-delay-load-import.md) opóźnienia ładowania msimg32.lib. Tak długo, jak aplikacja nie wywołuje jednej z tych metod podczas pracy w ramach systemu Windows NT 4.0 ani Windows 95, nie będzie próba załadowania msimg32.lib. Sprawdź, czy obsługi przezroczystości jest dostępne przy użyciu `CImage::IsTransparencySupported` metody.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 Aby skompilować aplikację, która wywołuje tych metod, Wstaw #define _WIN32_WINNT przed #including wszystkie nagłówki systemu, wskazująca, że wersja systemu Windows jest równa lub większa niż 5.0:  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 Jeśli aplikacja nie wymaga do uruchomienia na system operacyjny starszy niż Windows 2000 lub Windows 98, możesz połączyć się bezpośrednio z msimg32.lib bez użycia **/delayload**.  
  
 [CImage::Draw](../atl-mfc-shared/reference/cimage-class.md#draw) zachowuje się inaczej w przypadku użycia z systemu Windows 2000 i Windows 98, niż w systemie Windows NT 4.0 ani Windows 95.  
  
 Jeśli skompilować aplikację z zestawem _WIN32_WINNT na wartość mniejszą niż 0x0500, **rysowania** będzie działało, ale nie obsłuży przejrzystości automatycznie na komputerach z systemem Windows 2000 i Windows 98 i nowszych.  
  
 Jeśli kompilacja Twojej aplikacji z ustawioną 0x0500 _WIN32_WINNT lub większą, **rysowania** obsłuży przejrzystości automatycznie na komputerach z systemem Windows 2000 lub Windows 98 i nowszych. Może ona również działać, ale bez obsługi przezroczystości, z systemu Windows NT 4.0 i system operacyjny Windows 95; jednak należy użyć **/delayload** opóźnienia ładowania msimg32. LIB, jak opisano powyżej dla `AlphaBlend` i `TransparentBlt`.  
  
## <a name="see-also"></a>Zobacz też  
 [CImage — klasa](../atl-mfc-shared/reference/cimage-class.md)
