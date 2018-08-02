---
title: Dodawanie lub usuwanie ciągu | Dokumentacja firmy Microsoft
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
- strings [C++], adding to string tables
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90a470aa5bb1b24ab2fe549f098a83c29e5d0828
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464152"
---
# <a name="adding-or-deleting-a-string"></a>Dodawanie lub usuwanie ciągu
Można szybko wstawić nowe wpisy w tabeli ciągów za pomocą edytora ciągów. Nowych ciągów są umieszczane na końcu tabeli i podano następny dostępny identyfikator. Następnie można edytować właściwości Identyfikatora, wartość lub podpis w [okno właściwości](/visualstudio/ide/reference/properties-window) zgodnie z potrzebami.  
  
 Edytor ciągów zapewnia, że nie używasz Identyfikatora, który jest już używana. Wybranie Identyfikatora już w użyciu, edytor ciągów będzie powiadamiał, a następnie przypisz ogólny Unikatowy identyfikator, na przykład IDS_STRING58113.  
  
### <a name="to-add-a-string-table-entry"></a>Aby dodać wpis tabeli ciągów  
  
1.  Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Kliknij prawym przyciskiem myszy w tabeli ciągów, a następnie wybierz **nowy ciąg** z menu skrótów.  
  
3.  W **ciąg** edytora, wybierz opcję **identyfikator** z listy rozwijanej identyfikator lub wpisz identyfikator bezpośrednio od razu.  
  
4.  Edytuj **wartość**, jeśli to konieczne.  
  
5.  Wpisz wpis dla **podpis**.  
  
    > [!NOTE]
    >  Ciągów o wartości null są niedozwolone w tabelach ciągów Windows. Jeśli tworzysz wpis w tabeli ciągów, który jest pusty ciąg, zostanie wyświetlony komunikat z prośbą do "Wprowadź ciąg dla tego wpisu w tabeli."  
  
### <a name="to-delete-a-string-table-entry"></a>Aby usunąć wpis tabeli ciągów  
  
1.  Wybierz wpis, który chcesz usunąć.  
  
2.  Na **Edytuj** menu, kliknij przycisk **Usuń**.  
  
 \- lub —  
  
-   Kliknij prawym przyciskiem myszy ciągu chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.  
  
 \- lub —  
  
-   Naciśnij klawisz **Usuń** klucza.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework.* Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor ciągów](../windows/string-editor.md)   