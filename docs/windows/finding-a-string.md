---
title: Znajdowanie ciągów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3763baf0f085dc72040ab22c9efd38e8aa8068f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875737"
---
# <a name="finding-a-string"></a>Znajdowanie ciągów
Wyszukaj jeden lub więcej ciągów w tabeli ciągów i użyj [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) z **Znajdź w plikach** polecenia (**Edytuj** menu) można znaleźć wszystkich wystąpień ciągów które zgodne ze wzorcem.  
  
### <a name="to-find-a-string-in-the-string-table"></a>Aby znaleźć ciąg w tabeli ciągów  
  
1.  Otwórz tabeli ciągów, klikając odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Na **Edytuj** menu, kliknij przycisk **Znajdź i Zamień**, a następnie wybierz **znaleźć**.  
  
3.  W **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz podpis tekst lub identyfikator zasobu ciągu, który ma zostać znaleziony.  
  
4.  Wybierz jedno z **znaleźć** opcje.  
  
5.  Kliknij przycisk **Znajdź następny**.  
  
    > [!TIP]
    >  Aby użyć wyrażenia regularnego podczas wyszukiwania plików, użyj **Znajdź w plikach** polecenia. Wpisz wyrażenie regularne zgodne ze wzorcem lub kliknij przycisk z prawej strony **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwanie tekstu w **Znajdź** pole. Upewnij się, jeśli używasz wyrażeń regularnych, **Użyj: wyrażeń regularnych** pole wyboru jest zaznaczone.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych (te, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego), zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor ciągów](../windows/string-editor.md)   

