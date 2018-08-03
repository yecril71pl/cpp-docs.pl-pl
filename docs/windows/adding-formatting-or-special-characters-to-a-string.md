---
title: Dodawanie znaków specjalnych ani formatowania z ciągiem | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 35592793b0fe606d3b88bef900d528d2c1231406
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463843"
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>Porady: formatowanie i znaki w ciągu
### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Aby dodać znaków specjalnych ani formatowania na ciąg  
  
1.  Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Wybierz ciąg, który chcesz zmodyfikować.  
  
3.  W [okno właściwości](/visualstudio/ide/reference/properties-window), Dodaj dowolne sekwencje unikowe standardowych wymienionych poniżej, aby tekst w **podpis** pole i naciśnij klawisz **ENTER**.  
  
    |Aby uzyskać dostęp do tej|Wpisz to|  
    |-----------------|---------------|  
    |Nowy wiersz|\n|  
    |Powrót karetki|\r|  
    |Tab|\t|  
    |Ukośnik odwrotny (\\)|\\\|  
    |Znak ASCII|\ddd (Zapis ósemkowy)|  
    |alert (dzwonek)|\a|  
  
> [!NOTE]
>  Edytor ciągów nie obsługuje pełny zestaw znaki ucieczki przestają być ASCI. Można używać tylko wymienione powyżej.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework.* Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor ciągów](../windows/string-editor.md)   

