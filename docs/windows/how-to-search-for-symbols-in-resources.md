---
title: 'Porady: wyszukiwanie symboli w zasobach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3040e89ee4c729953c1a56f0c8728ba4d5b9d7b6
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570525"
---
# <a name="how-to-search-for-symbols-in-resources"></a>Porady: wyszukiwanie symboli w zasobach
### <a name="to-find-symbols-in-resources"></a>Aby znaleźć symboli w zasobach  
  
1.  Z **Edytuj** menu, wybierz **Znajdź Symbol**.  
  
2.  W [Znajdź Symbol — okno dialogowe](http://msdn.microsoft.com/63e93d9c-784f-418d-a76a-723da5ff5d96)w **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz klawisza skrótu do wyszukania (na przykład ID_ACCEL1).  
  
    > [!TIP]
    >  Aby użyć [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) wyszukiwania, należy użyć [Znajdź w plikach — polecenie](/visualstudio/ide/reference/find-command) z **Edytuj** menu zamiast **Znajdź Symbol**polecenia. Aby włączyć wyrażeń regularnych, konieczne jest posiadanie **użycia: wyrażeń regularnych** zaznaczone pole wyboru w [okno dialogowe Znajdź](http://msdn.microsoft.com/dad03582-4931-4893-83ba-84b37f5b1600). Następnie możesz kliknąć przycisk strzałki w dół po prawej stronie **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwany tekst w **Znajdź** pole.  
  
3.  Wybierz dowolny z **znaleźć** opcje.  
  
4.  Kliknij przycisk **Znajdź następny**.  
  
    > [!NOTE]
    >  Nie można wyszukiwać symbole w ciągu, akcelerator lub zasobów binarnych.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Instrukcje dotyczące ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości i [Instruktaż: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Symbole: Identyfikatory zasobów](../windows/symbols-resource-identifiers.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)