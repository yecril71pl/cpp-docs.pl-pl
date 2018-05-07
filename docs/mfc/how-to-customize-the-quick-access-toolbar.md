---
title: 'Porady: Dostosowywanie paska narzędzi Szybki dostęp | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0faa3a0fb66c4379824a6be190175b10e0415474
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Porady: dostosowywanie paska narzędzi Szybki dostęp
Szybki dostęp do paska narzędzi (QAT) jest paskiem narzędzi, który zawiera zestaw poleceń, które są albo wyświetlane obok przycisku aplikacji lub na kartach kategorii. Na poniższej ilustracji przedstawiono typowe narzędzi Szybki dostęp.  
  
 ![Narzędzi Szybki dostęp wstążki MFC](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")  
  
 Aby dostosować paska narzędzi Szybki dostęp, otwórz go w **właściwości** , zmodyfikuj jego poleceń, a następnie podglądu formantu wstążki.  
  
### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Aby otworzyć pasek narzędzi Szybki dostęp w oknie właściwości  
  
1.  W programie Visual Studio na **widoku** menu, kliknij przycisk **widok zasobów**.  
  
2.  W **widok zasobów**, kliknij dwukrotnie plik zasobu wstążki, aby go wyświetlić na powierzchni projektu.  
  
3.  Na powierzchni projektu, kliknij prawym przyciskiem myszy pasek narzędzi Szybki dostęp do menu, a następnie kliknij przycisk **właściwości**.  
  
## <a name="quick-access-toolbar-properties"></a>Właściwości paska narzędzi Szybki dostęp  
 W poniższej tabeli opisano właściwości paska narzędzi Szybki dostęp.  
  
|Właściwość|Definicja|  
|--------------|----------------|  
|Położenie QAT|Określa położenie paska narzędzi Szybki dostęp podczas uruchamiania aplikacji. Pozycja może być albo **powyżej** lub **poniżej** formantu wstążki.|  
|Elementy QAT|Określa polecenia, które są dostępne dla paska narzędzi Szybki dostęp.|  
  
#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Aby dodać lub usunąć polecenia na pasku narzędzi Szybki dostęp  
  
1.  W **właściwości** okna, kliknij przycisk **elementy QAT**, a następnie kliknij przycisk wielokropka **(...)** .  
  
2.  W **Edytor elementy QAT** okno dialogowe, użyj **Dodaj** i **Usuń** przycisków, aby zmodyfikować listę poleceń na pasku narzędzi Szybki dostęp.  
  
3.  Polecenie się na pasku narzędzi Szybki dostęp i menu paska narzędzi Szybki dostęp, zaznacz pole wyboru obok polecenia. Jeśli chcesz umieścić tylko w menu polecenie Wyczyść to pole.  
  
## <a name="previewing-the-ribbon"></a>Wyświetlanie podglądu wstążki  
 Szybki dostęp do narzędzi poleceń nie jest wyświetlana na powierzchni projektu. Aby je wyświetlić, możesz wyświetlić podgląd Wstążki lub uruchomić aplikację.  
  
#### <a name="to-preview-the-ribbon-control"></a>Aby wyświetlić podgląd formantu wstążki  
  
-   Na **paska narzędzi edytora wstążki**, kliknij przycisk **wstążki testu**.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

