---
title: Edytowanie interfejsu COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.editing.interfaces
dev_langs:
- C++
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd7a61593a1024c00c0fd0de6bd62ff3ee9323b3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33338685"
---
# <a name="editing-a-com-interface"></a>Edytowanie interfejsu COM
Za pomocą poleceń menu skrótów widoku klasy, można zdefiniować nowej metody i właściwości dla interfejsów COM w projektach Visual C++. Ponadto w przyborniku można zdefiniować zdarzeń dla formantów ActiveX.  
  
 ATL i MFC — klasy oparte na modelu COM obiektu można edytować implementację klasy, w tym samym czasie, aby edytować interfejs.  
  
> [!NOTE]
>  Dla interfejsów, które zostały zdefiniowane poza **Dodaj klasę** okno dialogowe, Visual C++ dodaje metody lub właściwości do pliku .idl, i dodanie wycinków kodu do klasy, które implementują metody, nawet jeśli interfejsy zostaną dodane ręcznie.  
  
 Następujących kreatorów trzy ułatwiają dostosowywanie istniejących interfejsów. Są one dostępne z widoku klasy:  
  
|Kreator|Typ projektu|  
|------------|------------------|  
|[Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md)|Projekty ATL ani MFC obsługi ATL. Kliknij prawym przyciskiem myszy interfejs, do którego chcesz dodać właściwości.<br /><br /> Visual C++ wykrywa typ projektu i odpowiednio modyfikuje opcje w Kreatorze dodawania właściwości:<br /><br /> — Dla dispinterfaces w przypadku projektów utworzonych za pomocą [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), wywoływania Kreatora dodawania właściwości udostępnia opcje określone z MFC.<br />— Dla interfejsów kontrolki MFC ActiveX Dodaj Kreatora właściwości zawiera listę standardowych metod i właściwości, które można stosować określony lub dostosować dla formantu.<br />— Dla wszystkich innych interfejsów kreatorów Dodaj właściwość opcje przydatne w większości sytuacji.|  
|[Kreator dodawania metody](../ide/add-method-wizard.md)|Projekty ATL ani MFC obsługi ATL. Kliknij prawym przyciskiem myszy interfejs, do której chcesz dodać metody.<br /><br /> Visual C++ wykrywa typ projektu i odpowiednio modyfikuje opcje w Kreatorze dodawania metody:<br /><br /> — Dla dispinterfaces w przypadku projektów utworzonych za pomocą [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator dodawania metody wywoływania udostępnia opcje określone z MFC.<br />— Dla interfejsów kontrolki MFC ActiveX Kreator dodawania metody zawiera listę standardowych metod i właściwości, które można stosować określony lub dostosować dla formantu.<br />— Dla wszystkich innych interfejsów **Dodaj metodę** kreatorów udostępniają opcje, które są przydatne w większości sytuacji.|  
  
 Ponadto można wdrożyć nowe interfejsy COM formantu prawym przyciskiem myszy obiekt klasy formantu w widoku klas, a następnie klikając polecenie [implementować interfejs](../ide/implement-interface-wizard.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z plikami zasobów](../windows/working-with-resource-files.md)   
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)