---
title: Dodawanie do ciągu znaków specjalnych ani formatowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 429ba8d836579bd3bc1d1dd8844494bf9cd17a7a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864600"
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>Porady: formatowanie i znaki w ciągu
### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Aby dodać formatowanie i znaki na ciąg  
  
1.  Otwórz tabeli ciągów, klikając odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Wybierz ciąg, który chcesz zmodyfikować.  
  
3.  W [okna właściwości](/visualstudio/ide/reference/properties-window), Dodaj dowolne standardowe unikowe wymienionych poniżej w tekście **podpis** pole i naciśnij klawisz **ENTER**.  
  
    |Aby uzyskać dostęp do tej|Wpisz to|  
    |-----------------|---------------|  
    |Nowy wiersz|\n|  
    |Powrót karetki|\r|  
    |Tab|\t|  
    |Ukośnik odwrotny (\\)|\\\|  
    |Znaków ASCII|\ddd (notation ósemkowe)|  
    |Alert (dzwonka)|\a|  
  
> [!NOTE]
>  Edytor ciągów nie obsługuje pełny zestaw znaków ASCI zmienionym znaczeniu. Można używać tylko wymienione powyżej.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych (te, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego), zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor ciągów](../windows/string-editor.md)   

