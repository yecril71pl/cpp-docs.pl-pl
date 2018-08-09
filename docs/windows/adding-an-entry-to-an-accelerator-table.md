---
title: Dodawanie wpisu do tabeli akceleratora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0c5e94913a705ac97407f82075ff9c83a12dd6b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642792"
---
# <a name="adding-an-entry-to-an-accelerator-table"></a>Dodawanie wpisu do Tabeli akceleratora
### <a name="to-add-an-entry-to-an-accelerator-table"></a>Aby dodać wpis do tabeli akceleratora  
  
1.  Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Kliknij prawym przyciskiem myszy w tabeli klawiszy skrótów, a następnie wybierz **nowy akcelerator** z menu skrótów, lub kliknij wpis pusty wiersz na końcu tabeli.  
  
3.  Wybierz [identyfikator](id-property.md) z listy rozwijanej w identyfikatorze pole lub wpisz nowy identyfikator w **identyfikator** pole.  
  
4.  Typ [klucz](../windows/accelerator-key-property.md) chcesz użyć jako akcelerator lub kliknij prawym przyciskiem myszy i wybrać **dalej wpisany klucz** z menu skrótów, aby ustawić kombinację klawiszy ( **dalej wpisany klucz** polecenia również dostępne z **Edytuj** menu).  
  
5.  Zmiana [modyfikator](../windows/accelerator-modifier-property.md) i [typu](../windows/accelerator-type-property.md), jeśli to konieczne.  
  
6.  Naciśnij klawisz **ENTER**.  
  
    > [!NOTE]
    >  Upewnij się, że wszystkie akceleratorów, jaką zdefiniujesz są unikatowe. Może mieć kilka kombinacji klawiszy przypisane do tego samego Identyfikatora przy użyciu efektu wpływu, na przykład **Ctrl** + **P** i **F8** zarówno można przypisać do ID_PRINT. Jednak masz kombinację klawiszy przypisane do więcej niż jeden identyfikator nie będzie działać poprawnie, na przykład **Ctrl** + **Z** przypisane do ID_SPELL_CHECK i ID_THESAURUS.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)