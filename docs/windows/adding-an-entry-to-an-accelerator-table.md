---
title: Dodawanie wpisu do tabeli akceleratora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fe2df81aae0b9b7232443de1db091a9cbb0c0d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-entry-to-an-accelerator-table"></a>Dodawanie wpisu do Tabeli akceleratora
### <a name="to-add-an-entry-to-an-accelerator-table"></a>Aby dodać wpis do tabeli akceleratora  
  
1.  Otwórz tabeli akceleratora klikając odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Kliknij prawym przyciskiem myszy wewnątrz tabeli klawiszy skrótów i wybierz polecenie **nowy akcelerator** z menu skrótów, lub kliknij wpis pustego wiersza w dolnej części tabeli.  
  
3.  Wybierz [identyfikator](id-property.md) z listy rozwijanej w identyfikatorze pola lub wpisz nową nazwę w **identyfikator** pole.  
  
4.  Typ [klucza](../windows/accelerator-key-property.md) ma być używany jako akcelerator lub kliknij prawym przyciskiem myszy i wybierz polecenie **dalej wpisany klucz** z menu skrótów, aby ustawić kombinacja klawiszy ( **dalej wpisany klucz** polecenie jest również dostępne z **Edytuj** menu).  
  
5.  Zmień [modyfikator](../windows/accelerator-modifier-property.md) i [typu](../windows/accelerator-type-property.md), jeśli to konieczne.  
  
6.  Naciśnij klawisz **ENTER**.  
  
    > [!NOTE]
    >  Upewnij się, że wszystkie akceleratorów, definiowane są unikatowe. Może mieć kilka kombinacji klawiszy przypisane do tego samego Identyfikatora z dotknięty wpływu, na przykład CTRL + P i F8 zarówno można przypisać do ID_PRINT. Jednak o kombinację klawiszy przypisany do więcej niż jeden identyfikator nie będzie działać prawidłowo, na przykład CTRL + Z przypisane do ID_SPELL_CHECK i ID_THESAURUS.  
  

  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)