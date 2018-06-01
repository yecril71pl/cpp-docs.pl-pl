---
title: Implementowanie interfejsu (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 309ae9dc576f93574836ab4916e87c5232b37a6c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33332770"
---
# <a name="implementing-an-interface-visual-c"></a>Implementowanie interfejsu (Visual C++)
Aby zaimplementować interfejs, musi utworzono projekt jako aplikacji ATL COM lub aplikacji z obsługą ATL MFC. Można użyć [Kreator projektu ATL](../atl/reference/atl-project-wizard.md) Aby utworzyć aplikację ATL lub [Dodaj obiekt ATL do aplikacji MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) ATL Obsługa aplikacji MFC.  
  
 Po utworzeniu projektu, aby zaimplementować interfejs, najpierw należy dodać obiekt ATL. Zobacz [Dodawanie obiektów i kontroli w celu Projekt ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) listę kreatorów, które dodać obiekty do projektu ATL.  
  
> [!NOTE]
>  Kreator nie obsługuje okien dialogowych ATL, za pomocą biblioteki ATL obiekty wydajności i liczniki wydajności usługi XML sieci Web.  
  
 Jeśli użytkownik [Dodawanie formantu ATL](../atl/reference/adding-an-atl-control.md), można określić, czy do implementacji interfejsów domyślne, wymienionych w [interfejsów](../atl/reference/interfaces-atl-control-wizard.md) to kreatora i zdefiniowanych w atlcom.h.  
  
 Po dodaniu do obiektu lub kontrolki, można zaimplementować inne interfejsy, znajduje się w dowolnej bibliotece dostępnego w za pomocą Kreatora interfejsu wdrożenia.  
  
 Jeśli dodajesz nowy interfejs, należy dodać go ręcznie do pliku .idl projektu. Zobacz [dodawanie nowy interfejs w projekcie ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md) Aby uzyskać więcej informacji.  
  
### <a name="to-implement-an-interface"></a>Aby zaimplementować interfejs  
  
1.  W widoku klas kliknij prawym przyciskiem myszy nazwę klasy dla obiekt ATL.  
  
2.  Kliknij przycisk **Dodaj** z menu skrótów, a następnie kliknij przycisk **implementuj interfejs** do wyświetlenia [Kreator implementacji interfejsu](../ide/implement-interface-wizard.md).  
  
3.  Wybierz interfejsy do implementacji z bibliotek odpowiedniego typu, a następnie kliknij przycisk **Zakończ**.  
  
4.  W widoku klas, rozwiń węzeł baz obiektu i interfejsy węzeł, aby zobaczyć interfejs został zaimplementowany, a następnie rozwiń węzeł interfejsu, aby zobaczyć jego dostępne właściwości, metod i zdarzeń.  
  
    > [!NOTE]
    >  Można również użyć [przeglądarki obiektów](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) do sprawdzenia członków interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Edytowanie interfejsu COM](../ide/editing-a-com-interface.md)