---
title: "Ustawianie właściwości klawiszy skrótów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 83eea84c89a9f9873b687333b7454d9f3c9c41b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setting-accelerator-properties"></a>Ustawianie właściwości klawiszy skrótów
Można ustawić właściwości klawiszy skrótów w [okna właściwości](/visualstudio/ide/reference/properties-window) w dowolnym momencie. Edytor klawiszy skrótów umożliwia także modyfikowanie właściwości klawiszy skrótów w tabeli akceleratora. Zmiany wprowadzone przy użyciu okna właściwości lub Edytor klawiszy skrótów mają ten sam rezultat: zmiany są natychmiast odzwierciedlone w tabeli akceleratora.  
  
 Istnieją trzy właściwości dla każdego akceleratora [identyfikator](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   [Modifier — właściwość](../windows/accelerator-modifier-property.md) formant kombinacji z klawiszem akceleratora.  
  
    > [!NOTE]
    >  W oknie właściwości tej właściwości jest wyświetlany jako trzech oddzielnych właściwości logiczne, które mogą być kontrolowane niezależnie: Alt, Ctrl i Shift.  
  
-   [Właściwości kluczowej](../windows/accelerator-key-property.md) ustawia rzeczywisty klucz do użycia jako akcelerator.  
  
-   [Type — właściwość](../windows/accelerator-type-property.md) Określa, czy klucz jest interpretowana jako wirtualny (VIRTKEY) lub ASCII/ANSI.  
  

  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)   
 [Edytory zasobów](../windows/resource-editors.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)