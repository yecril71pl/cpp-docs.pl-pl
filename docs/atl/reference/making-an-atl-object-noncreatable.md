---
title: "Tworzenie noncreatable — obiekt ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.ATL.objects
dev_langs: C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38aa9f5fae45c9d5fa1e413763bd5fa2e65ab795
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="making-an-atl-object-noncreatable"></a>Tworzenie noncreatable — obiekt ATL
Atrybuty obiektu oparty na ATL COM można zmienić tak, aby klient nie można bezpośrednio utworzyć obiekt. W takim przypadku obiekt będzie można zwrócony przez wywołanie metody na innym obiekcie zamiast bezpośrednio tworzone.  
  
### <a name="to-make-an-object-noncreatable"></a>Aby noncreatable — obiekt  
  
1.  Usuń [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) dla obiekt. Obiekt noncreatable — ale formant, który ma zostać zarejestrowany, Zamień OBJECT_ENTRY_AUTO z [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).  
  
2.  Dodaj [noncreatable —](../../windows/noncreatable.md) do klasy coclass w pliku .idl. Na przykład:  
  
 ```  
 [  
    uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
 {  
 [default] interface IMyInterface;  
 }  
 ```  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programowanie za pomocą ALT i C Run-Time kodu](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Podstawowe informacje na temat ATL COM — obiekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

