---
title: "Dodawanie lub usuwanie ciągu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.string
dev_langs: C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd4d4f1b6132ed5e44134f502fe673030306b14b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="adding-or-deleting-a-string"></a>Dodawanie lub usuwanie ciągu
Można szybko wstawić nowe wpisy w tabeli ciągów za pomocą edytora ciągów. Nowe parametry są umieszczane na koniec tabeli i podano następny dostępny identyfikator. Następnie można edytować właściwości Identyfikatora, wartość lub podpisu w [okna właściwości](/visualstudio/ide/reference/properties-window) zgodnie z potrzebami.  
  
 Edytor ciągów upewnia się, że nie używasz identyfikator, który jest już używana. Wybranie Identyfikatora już w użyciu, edytor ciągów zostanie wyświetlona, a następnie przypisz ogólnego Unikatowy identyfikator, na przykład IDS_STRING58113.  
  
### <a name="to-add-a-string-table-entry"></a>Aby dodać wpis do tabeli ciągów  
  
1.  Otwórz tabeli ciągów, klikając odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Kliknij prawym przyciskiem myszy w tabeli ciągów i wybierz polecenie **nowe parametry** z menu skrótów.  
  
3.  W **ciąg** edytora, wybierz opcję **identyfikator** z listy rozwijanej identyfikator lub wpisz identyfikator bezpośrednio na miejscu.  
  
4.  Edytuj **wartość**, jeśli to konieczne.  
  
5.  Wpisz hasło dla **podpis**.  
  
    > [!NOTE]
    >  Ciągów o wartości null są niedozwolone w tabelach ciągów systemu Windows. Jeśli utworzysz wpis w tabeli ciągów, która jest pustym ciągiem, zostanie wyświetlony komunikat z pytaniem do "Wprowadź ciąg dla tego wpisu tabeli."  
  
### <a name="to-delete-a-string-table-entry"></a>Aby usunąć wpis tabeli ciągów  
  
1.  Wybierz wpis, który chcesz usunąć.  
  
2.  Na **Edytuj** menu, kliknij przycisk **usunąć**.  
  
 \-lub -  
  
-   Kliknij prawym przyciskiem myszy ciągu chcesz usunąć, a następnie wybierz pozycję **usunąć** z menu skrótów.  
  
 \-lub -  
  
-   Naciśnij klawisz **usunąć** klucza.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych (te, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego), zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor ciągów](../windows/string-editor.md)   

