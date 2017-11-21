---
title: Opcje, Kreator formantu ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.options
dev_langs: C++
helpviewer_keywords: ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 314f0c7675212ad1f453da189d6483fc9b8284c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="options-atl-control-wizard"></a>Opcje, Kreator formantu ATL
Tutaj należy wstawić "Wyszukiwanie" podsumowania.  
  
 Ta strona kreatora służy do definiowania typu formantu, który tworzysz i zawiera poziom obsługi interfejsu.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Typ formantu**  
 Rodzaj kontroli, którą chcesz utworzyć.  
  
-   **Formant standardowy: formantu ActiveX.**  
  
-   **Formantu złożonego**: formantu ActiveX, który może zawierać (podobnie do okna dialogowego) innych formantów ActiveX lub formantów systemu Windows. Formantu złożonego obejmuje następujące funkcje:  
  
    -   Szablon dla okna dialogowego, który implementuje formantu złożonego.  
  
    -   Zasób niestandardowy rejestru, w którym automatycznie rejestruje formantu złożonego, gdy została wywołana.  
  
    -   Klasy C++, który implementuje formantu złożonego.  
  
    -   Interfejs COM udostępnianych przez formantu złożonego.  
  
    -   Strona testowa HTML zawierający formantu złożonego.  
  
     Domyślnie ten formant ustawia [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) wartość "prawda", aby wskazać, że jest to okna formantu. Implementuje mapy ujścia. Aby uzyskać więcej informacji, zobacz [pomocy technicznej dla DHTML](../../atl/atl-support-for-dhtml-controls.md).  
  
-   **Formant DHTML**: Formant ATL DHTML określa interfejs użytkownika, przy użyciu języka HTML. Klasa interfejsu użytkownika DHTML zawiera mapy COM. Domyślnie ten formant ustawia [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) wartość "prawda", aby wskazać, że jest to okna formantu.  
  
     Aby uzyskać więcej informacji, zobacz [określający elementy projektu kontroli DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
 **Minimalny formantu**  
 Obsługuje tylko interfejsy, które są całkowicie wymagane przez większość kontenerów. Można ustawić **minimalnego kontroli** dla dowolnego typu kontrolki: można utworzyć minimalnego formantu standardowego, minimalnym formantu złożonego lub minimalnego formantu DHTML.  
  
 **Agregacji**  
 Dodaje obsługę funkcji agregacji dla formantu, który tworzysz. Aby uzyskać więcej informacji, zobacz [agregacji](../../atl/aggregation.md).  
  
-   **Tak**: Tworzenie formantu, który może być agregowany.  
  
-   **Nie**: Tworzenie formantu nie można agregować.  
  
-   **Tylko**: Tworzenie formantu, który można wdrożyć tylko za pośrednictwem agregacji.  
  
 **Model wątkowości**  
 Określa, że model wątkowy używany przez formant.  
  
-   **Pojedynczy**: formantu zostanie uruchomiony tylko w podstawowym wątku com..  
  
-   **Apartamentu**: formantu można tworzyć w dowolnym komórka wątku pojedynczego. Domyślnie.  
  
 **Interfejs**  
 Typ interfejsu, tego formantu przedstawia do kontenera.  
  
-   **Podwójna**: tworzy interfejs, który udostępnia właściwości i metody, za pomocą `IDispatch` i bezpośrednio za pomocą VTBL.  
  
-   **Niestandardowe**: tworzy interfejs, który udostępnia metody bezpośrednio za pomocą VTBL.  
  
     W przypadku wybrania **niestandardowy**, następnie można określić, czy kontrolka jest **zgodny automatyzacji**. W przypadku wybrania **zgodny automatyzacji**, następnie Kreator dodaje [oleautomation](../../windows/oleautomation.md) atrybutu interfejsu w IDL, i interfejsu może być organizowany przy użyciu uniwersalnych Organizator w oleaut32.dll. Zobacz [organizowanie szczegóły](http://msdn.microsoft.com/library/windows/desktop/ms692621) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
     Ponadto w przypadku wybrania **zgodny automatyzacji**, wszystkie parametry dla wszystkich metod w formancie musi być **VARIANT** zgodne.  
  
 **Obsługa**  
 Ustawia dodatkowe dodatkowe wsparcie dla formantu.  
  
-   **Punkty połączenia**: włącza punktów połączeń dla obiekt dokonując pochodzi od klasy do obiektu [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) do uwidacznia interfejs źródłowy.  
  
-   **Licencjonowane**: dodaje obsługę do formantu [licencjonowania](http://msdn.microsoft.com/library/windows/desktop/ms690543). Licencjonowane formanty może być obsługiwany tylko, jeśli komputer kliencki ma odpowiednią licencję.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator formantu ATL](../../atl/reference/atl-control-wizard.md)

