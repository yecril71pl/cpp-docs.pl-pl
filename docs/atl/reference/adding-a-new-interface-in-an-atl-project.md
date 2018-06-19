---
title: Dodawanie nowego interfejsu w Projekt ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.interface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2c9d0ef4c14760d596a4aa26fa2a929da26c67b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356748"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Dodawanie nowego interfejsu w Projekt ATL
Po dodaniu interfejsu do obiektu lub formant tworzenia funkcji poza zastąpić jej metodą zastępczą dla każdej metody w tym interfejsie. W obiekcie lub kontrolki można dodać tylko interfejsy aktualnie znalezionych w istniejącej biblioteki typów. Ponadto musi implementować klasę, w którym można dodać interfejs [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) makro lub, jeśli projekt jest przypisane, musi on mieć `coclass` atrybutu.  
  
 Można dodać nowy interfejs do swojego formantu w jeden z dwóch sposobów: ręcznie lub za pomocą kreatorów kodu w widoku klas.  
  
### <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Do użycia kreatorów kodu w widoku klas, aby dodać interfejs do istniejącego obiektu lub formantu  
  
1.  W [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę klasy formantu. Na przykład Pełna kontrola lub formantu złożonego lub innych implementujący makro BEGIN_COM_MAP w pliku nagłówka klasy formantu.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **implementuj interfejs**.  
  
3.  Wybierz interfejsy do zaimplementowania w [Kreator implementuje interfejs](../../ide/implement-interface-wizard.md). Jeśli interfejs nie istnieje w dowolnej dostępnej biblioteki typów, następnie należy dodać go ręcznie do pliku .idl.  
  
### <a name="to-add-a-new-interface-manually"></a>Aby ręcznie dodać nowy interfejs  
  
1.  Dodaj definicję nowego interfejsu do pliku .idl.  
  
2.  Pochodzi z obiektu lub formantu w interfejsie.  
  
3.  Utwórz nową [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) interfejsu lub, jeśli ma atrybut projekt, Dodaj `coclass` atrybutu.  
  
4.  Implementuje metody interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programowanie za pomocą ALT i C Run-Time kodu](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Podstawowe informacje na temat ATL COM — obiekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

