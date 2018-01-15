---
title: 'Porady: wyszukiwanie symboli w zasobach | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 154c7a7284272ceef7a3e2d82fcd90d05069b7fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-search-for-symbols-in-resources"></a>Porady: wyszukiwanie symboli w zasobach
### <a name="to-find-symbols-in-resources"></a>Aby znaleźć symboli w zasobach  
  
1.  Z **Edytuj** menu, wybierz **Znajdź Symbol**.  
  
2.  W [Znajdź Symbol — okno dialogowe](http://msdn.microsoft.com/en-us/63e93d9c-784f-418d-a76a-723da5ff5d96)w **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz klawisz skrótu, który ma zostać znaleziony (na przykład ID_ACCEL1).  
  
    > [!TIP]
    >  Aby użyć [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) wyszukiwania, należy użyć [Znajdź w plikach — polecenie](/visualstudio/ide/reference/find-command) z **Edytuj** menu zamiast **Znajdź Symbol**polecenia. Aby włączyć wyrażeń regularnych, musisz mieć **użycia: wyrażeń regularnych** zaznaczone pole wyboru w [okno dialogowe Znajdź](http://msdn.microsoft.com/en-us/dad03582-4931-4893-83ba-84b37f5b1600). A następnie kliknąć przycisk strzałki w prawo o **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwanie tekstu w **Znajdź** pole.  
  
3.  Wybierz jedno z **znaleźć** opcje.  
  
4.  Kliknij przycisk **Znajdź następny**.  
  
    > [!NOTE]
    >  Nie można wyszukać symbole w ciąg znaków, skrótów lub zasobów binarnych.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje o ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów wyświetlania statycznych zasobów i przydzielanie zasobów ciągów do właściwości oraz [wskazówki: przy użyciu zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Symbole: Identyfikatory zasobów](../windows/symbols-resource-identifiers.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)