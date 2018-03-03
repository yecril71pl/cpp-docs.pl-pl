---
title: "Właściwość klawisza skrótu | Dokumentacja firmy Microsoft"
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
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 365960717f5fe4cedf79615fd3087bc89d6b531c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-key-property"></a>Właściwość klawisza skrótu
Dostępne są następujące wpisy prawne dla właściwości klucza w tabeli akceleratora:  
  
-   Liczba całkowita między 0 a 255 w formacie dziesiętnym. Wartość określa, czy wartość jest traktowany jako ASCII lub ANSI w następujący sposób:  
  
    -   Cyfr zawsze będą interpretowane jako odpowiedniego klucza, a nie jako wartości ASCII lub ANSI.  
  
    -   Wartości z zakresu od 1 do 26, gdy przed zerami, są interpretowane jako ^ od A do ^ Z, który reprezentuje wartość ASCII litery alfabetu po naciśnięciu z wciśnięty klawisz CTRL.  
  
    -   Wartości z 27-32 zawsze będą interpretowane jako wartości dziesiętne trzycyfrowa 027 za pośrednictwem 032.  
  
    -   Wartości z 033 do 255, czy poprzedzony 0 nie będą interpretowane jako wartości ANSI.  
  
-   Znak pojedynczego klawiatury. Wielkie litery A - Z lub cyfry 0 - 9 mogą być ASCII lub wirtualny wartości klucza. inny znak jest tylko ASCII.  
  
-   Klawiatury pojedynczy znak z zakresu A - Z (tylko wielkie litery), poprzedzony daszek (^) (na przykład ^ C). Wprowadza wartość ASCII klucza, gdy zostanie naciśnięty z wciśnięty klawisz CTRL.  
  
    > [!NOTE]
    >  Podczas wprowadzania wartości ASCII, opcje właściwości modyfikator są ograniczone. Tylko klucza kontroli dostępne do użycia jest klawisz ALT.  
  
-   Wszystkie prawidłowe wirtualny identyfikator klawisza. Pole listy rozwijanej klucza w tabeli akceleratora zawiera standardowe wirtualnych identyfikatorów klucza.  
  
    > [!TIP]
    >  Innym sposobem definiowania klawiszem skrótu jest kliknij prawym przyciskiem myszy wpis lub wiele wpisów w tabeli akceleratora, wybierz **dalej wpisany klucz** z menu skrótów i naciśnij klawisze lub kombinacje klawiszy na klawiaturze. **Dalej wpisany klucz** polecenia jest również dostępna z **Edytuj** menu.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)   
 [Edytowanie w tabeli akceleratora](../windows/editing-in-an-accelerator-table.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)