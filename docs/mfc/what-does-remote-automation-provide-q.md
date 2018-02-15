---
title: Co oferuje zdalna automatyzacja? | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Remote Automation, DCOM
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4a82b26a1e6c208a584dfd19ebfd4530b4bdf76
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="what-does-remote-automation-provide"></a>Co oferuje zdalna automatyzacja?
Automatyzacja zdalna umożliwia programom wywołania `IDispatch` implementacje na jednej maszynie z innej. Obsługuje ona również inne interfejsy wymagane przez automatyzację, w szczególności **interfejsu IEnumVARIANT** kolekcji pomocy technicznej. Nie zapewnia możliwość dystrybucji innego interfejsu COM (z wyjątkiem **IUnknown**, oczywiście) i jak regularne automatyzacji zawiera obsługi organizowania tylko dla tych typów danych obsługiwanych przez automatyzację.  
  
 Ten zbiór urządzeń umożliwia programowi dostęp do metody i właściwości, w tym te, które zwracają kolekcje lub dodatkowe obiekty automatyzacji, uruchomione w węźle sieci dostępem do obiektu. Jeśli komputer kliencki działa również odpowiedniego oprogramowania, jest możliwe do wywołania zwrotnego do klienta, ponownie przy użyciu funkcji automatyzacji (to działa 32-bitowe i 64-bitowe tylko dla klientów, a jest podobny do zdarzeń, chociaż nie używa serwera Ten sam mechanizm).  
  
 Dla aplikacji, aby działać jako serwer automatyzacji zdalnej, musi zostać wdrożona jako plik wykonywalny (to znaczy jako "serwera", a nie jako "serwera inproc").  
  
## <a name="see-also"></a>Zobacz też  
 [Gdzie automatyzacji zdalnej pasują do](where-does-remote-automation-fit-in-q.md)   
 [Historia modelu DCOM](../mfc/history-of-dcom.md)
