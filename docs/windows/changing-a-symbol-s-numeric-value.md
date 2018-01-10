---
title: "Zmiana symbolu &#39; wartość liczbową s | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing.value
dev_langs: C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce2c846d844b79a6ff054bb6c209d1f4653a26d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changing-a-symbol39s-numeric-value"></a>Zmiana symbolu &#39; wartość liczbową s
Symbole skojarzone z pojedynczego zasobu, można użyć [okna właściwości](/visualstudio/ide/reference/properties-window) Aby zmienić wartość symbolu. Można użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) zmianę wartości symboli nie jest aktualnie przypisana do zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).  
  
### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Aby zmienić wartość symbolu przypisane do pojedynczego zasobu lub obiektu  
  
1.  W [widok zasobów](../windows/resource-view-window.md), wybierz zasób.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W **właściwości** wpisz nazwę symbolu następuje znak równości i całkowitą **identyfikator** pola, na przykład:  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 Nowa wartość jest przechowywane w plik nagłówka symbolu przy następnym Zapisz projekt. Tylko nazwa symbolu pozostaje widoczna w polu Identyfikator; znak równości i wartość nie są wyświetlane po ich są weryfikowane.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje o ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów wyświetlania statycznych zasobów i przydzielanie zasobów ciągów do właściwości oraz [wskazówki: przy użyciu zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md)   
 [Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)