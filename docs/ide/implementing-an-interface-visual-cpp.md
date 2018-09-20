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
ms.openlocfilehash: 4227f566d655911553baeb5e8162f13bc9994130
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395534"
---
# <a name="implementing-an-interface-visual-c"></a>Implementowanie interfejsu (Visual C++)

Aby zaimplementować interfejs, musi utworzono projekt jako aplikację ATL COM lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

Po utworzeniu projektu, aby zaimplementować interfejs, należy najpierw dodać obiektu ATL. Zobacz [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) listę kreatorzy dodawania obiektów do projektu ATL.

> [!NOTE]
>  Kreator nie obsługuje okna dialogowe ATL, usługi XML sieci Web przy użyciu biblioteki ATL, obiekty wydajności i liczników wydajności.

Jeśli użytkownik [Dodawanie kontrolki ATL](../atl/reference/adding-an-atl-control.md), można określić, czy do implementacji interfejsów domyślny, na [interfejsów](../atl/reference/interfaces-atl-control-wizard.md) stronie oznacza pracę kreatora i zdefiniowaną w atlcom.h.

Po dodaniu obiektu lub formantu, można zaimplementować innych interfejsów znajduje się w dowolnej bibliotece dostępnych typów za pomocą Kreatora implementacji interfejsu.

W przypadku dodawania nowego interfejsu należy go ręcznie dodać do pliku .idl projektu. Zobacz [Dodawanie nowego interfejsu w projekcie ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md) Aby uzyskać więcej informacji.

### <a name="to-implement-an-interface"></a>Aby zaimplementować interfejs

1. W widoku klas kliknij prawym przyciskiem myszy nazwę klasy dla obiektu ATL.

1. Kliknij przycisk **Dodaj** z menu skrótów, a następnie kliknij przycisk **implementuj interfejs** do wyświetlenia [Kreator implementacji interfejsu](../ide/implement-interface-wizard.md).

1. Wybierz interfejsy do implementacji z bibliotek odpowiedniego typu, a następnie kliknij przycisk **Zakończ**.

1. W widoku klas, rozwiń węzeł bazy obiektu i języka node interfejsów, aby wyświetlić interfejs został zaimplementowany, a następnie rozwiń węzeł interfejsu, aby wyświetlić jego dostępnych właściwości, metody i zdarzenia.

   > [!NOTE]
   > Można również użyć [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code) zbadanie składowych interfejsu.

## <a name="see-also"></a>Zobacz też

[Tworzenie interfejsu COM](../ide/creating-a-com-interface-visual-cpp.md)<br>
[Edytowanie interfejsu COM](../ide/editing-a-com-interface.md)