---
title: Co oferuje zdalna automatyzacja? | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, DCOM
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6766b2fcc5d277b86f979252bf22e6ae343e608e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="what-does-remote-automation-provide"></a>Co oferuje zdalna automatyzacja?
Automatyzacja zdalna umożliwia programom wywołania `IDispatch` implementacje na jednej maszynie z innej. Obsługuje ona również inne interfejsy wymagane przez automatyzację, w szczególności **interfejsu IEnumVARIANT** kolekcji pomocy technicznej. Nie zapewnia możliwość dystrybucji innego interfejsu COM (z wyjątkiem **IUnknown**, oczywiście) i jak regularne automatyzacji zawiera obsługi organizowania tylko dla tych typów danych obsługiwanych przez automatyzację.  
  
 Ten zbiór urządzeń umożliwia programowi dostęp do metody i właściwości, w tym te, które zwracają kolekcje lub dodatkowe obiekty automatyzacji, uruchomione w węźle sieci dostępem do obiektu. Jeśli komputer kliencki działa również odpowiedniego oprogramowania, jest możliwe do wywołania zwrotnego do klienta, ponownie przy użyciu funkcji automatyzacji (to działa 32-bitowe i 64-bitowe tylko dla klientów, a jest podobny do zdarzeń, chociaż nie używa serwera Ten sam mechanizm).  
  
 Dla aplikacji, aby działać jako serwer automatyzacji zdalnej, musi zostać wdrożona jako plik wykonywalny (to znaczy jako "serwera", a nie jako "serwera inproc").  
  
## <a name="see-also"></a>Zobacz też  
 [Gdzie automatyzacji zdalnej pasują do](where-does-remote-automation-fit-in-q.md)   
 [Historia modelu DCOM](../mfc/history-of-dcom.md)
