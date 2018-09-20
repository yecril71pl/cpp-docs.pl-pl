---
title: Implementacja punktu połączenia (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bba7fdfd44b0a0a97a6d110d2a44b492e1ca449
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429334"
---
# <a name="implementing-a-connection-point-visual-c"></a>Implementacja punktu połączenia (Visual C++)

Aby zaimplementować za pomocą Kreatora punktu połączenia implementacji punktu połączenia, musi utworzono projekt jako aplikacji ATL COM lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

> [!NOTE]
>  Aby uzyskać informacji dotyczących implementowania punkty połączenia do projektu MFC, zobacz [punkty połączenia](../mfc/connection-points.md).

Po utworzeniu projektu, aby zaimplementować punkt połączenia należy najpierw dodać obiektu ATL. Zobacz [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) listę kreatorzy dodawania obiektów do projektu ATL.

> [!NOTE]
>  Kreator nie obsługuje okna dialogowe ATL, usług sieci Web XML utworzone za pomocą aplikacji serwera ATL. obiekty wydajności i liczników wydajności.

Obiekt łączności (źródła) mogą uwidocznić punkt połączenia dla każdego z jego interfejsów wychodzących. Każdego interfejsu wychodzącego może być implementowana przez klienta do obiektu (ujścia). Aby uzyskać więcej informacji, zobacz [punkty połączenia ATL](../atl/atl-connection-points.md).

### <a name="to-implement-a-connection-point"></a>Aby zaimplementować punktu połączenia

1. W widoku klas kliknij prawym przyciskiem myszy nazwę klasy dla obiektu ATL.

1. Kliknij przycisk **Dodaj** z menu skrótów, a następnie kliknij przycisk **Dodawanie punktów połączenia** do wyświetlenia [Kreator implementacji punktu połączenia](../ide/implement-connection-point-wizard.md).

1. Wybierz interfejsy punktu połączenia, aby zaimplementować z bibliotek odpowiedniego typu, a następnie kliknij przycisk **Zakończ**.

1. W widoku klas należy zbadać klasy serwera proxy, utworzone dla każdego punktu połączenia. Klasy są traktowane jako CProxy*InterfaceName*\<T > i są uzyskiwane z [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).

1. Kliknij dwukrotnie klasy punktów połączenia do wyświetlenia definicję klasy punktu połączenia.

   - W przypadku zaimplementowania punktu połączenia dla interfejsu własny projekt, zostanie wyświetlona następująca definicja

        ```
        template< class T >
        class CProxyInterfaceName :
           public IConnectionPointImpl< T, &IID_InterfaceName >
        {
        public:
        };
        ```

         If you implement a local interface, methods and properties appear in the class body.

   - W przypadku zaimplementowania punktu połączenia dla innego interfejsu definicja zawiera metod tego interfejsu, każdy poprzedzone `Fire_`.

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Dodawanie punktów połączenia do obiektu](../atl/adding-connection-points-to-an-object.md)