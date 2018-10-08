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
ms.openlocfilehash: f660f9d69fc787384fcfbec37caec0064a58ec29
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861346"
---
# <a name="editing-a-com-interface"></a>Edytowanie interfejsu COM

Za pomocą poleceń menu skrótów w widoku klas, można zdefiniować nowej metody i właściwości dla interfejsów COM w projektach języka Visual C++. Ponadto z przybornika, można zdefiniować zdarzenia dla formantów ActiveX.

ATL i MFC oparte na modelu COM klas obiektów można edytować implementację klasy, w tym samym czasie edytowania interfejsu.

> [!NOTE]
>  Dla interfejsów, które zostały zdefiniowane poza **Dodaj klasę** okno dialogowe, Visual C++ dodaje metody lub właściwości do pliku .idl i dodanie klasy zastępcze dla klas, które implementują metody, nawet wtedy, gdy interfejsy są dodawane ręcznie.

Następujących kreatorów trzy pomóc dostosować istniejące interfejsy. Są one dostępne z widoku klasy:

|Kreator|Typ projektu|
|------------|------------------|
|[Kreator dodawania właściwości](../ide/names-add-property-wizard.md)|Projekty ATL lub MFC, obsługa ATL. Kliknij prawym przyciskiem myszy interfejs, do którego chcesz dodać właściwość.<br /><br />Visual C++ wykrywa typ projektu i odpowiednio modyfikuje opcje w Kreatorze dodawania właściwości:<br /><br />– W przypadku dispinterfaces w projekty utworzone za pomocą [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), wywoływanie Kreator dodawania właściwości udostępnia opcje, które określone z MFC.<br />– W przypadku interfejsów kontrolki MFC ActiveX Kreator dodawania właściwości zawiera listę podstawowych metod i właściwości, które mogą używać zgodnie z postanowieniami lub dostosowywanie kontrolki.<br />— Dla wszystkich innych interfejsów kreatory Dodaj właściwość zapewniają przydatne w większości sytuacji opcje.|
|[Kreator dodawania metody](../ide/add-method-wizard.md)|Projekty ATL lub MFC, obsługa ATL. Kliknij prawym przyciskiem myszy interfejs, do którego chcesz dodać metody.<br /><br />Visual C++ wykrywa typ projektu i odpowiednio modyfikuje opcje w Kreatorze dodawania metody:<br /><br />– W przypadku dispinterfaces w projekty utworzone za pomocą [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator dodawania metody wywoływania udostępnia opcje, które określone z MFC.<br />– W przypadku interfejsów kontrolki MFC ActiveX Kreator dodawania metody zawiera listę podstawowych metod i właściwości, które mogą używać zgodnie z postanowieniami lub dostosowywanie kontrolki.<br />— Dla wszystkich innych interfejsów **Dodaj metodę** kreatorów udostępniają opcje przydatne w większości sytuacji.|

Ponadto można wdrożyć nowe interfejsy na kontrolki COM, klikając prawym przyciskiem myszy obiekt klasy formantu w widoku klas i klikając [implementować interfejs](../ide/implement-interface-wizard.md).

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br>
[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Typy projektów Visual C++](../ide/visual-cpp-project-types.md)