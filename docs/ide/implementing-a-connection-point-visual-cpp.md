---
title: Implementacja punktu połączenia
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.cp.overview
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 7afa61246c5251936967e281f7237dc37e5be045
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693285"
---
# <a name="implement-a-connection-point"></a>Implementacja punktu połączenia

Aby zaimplementować za pomocą Kreatora punktu połączenia implementacji punktu połączenia, musi utworzono projekt jako aplikacji ATL COM lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

> [!NOTE]
> Aby uzyskać informacji dotyczących implementowania punkty połączenia do projektu MFC, zobacz [punkty połączenia](../mfc/connection-points.md).

Po utworzeniu projektu, aby zaimplementować punkt połączenia należy najpierw dodać obiektu ATL. Zobacz [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) listę kreatorzy dodawania obiektów do projektu ATL.

> [!NOTE]
> Kreator nie obsługuje okna dialogowe ATL, usług sieci Web XML utworzone za pomocą aplikacji serwera ATL. obiekty wydajności i liczników wydajności.

Obiekt łączności (źródła) można wyświetlić punkt połączenia dla każdego z jego interfejsów wychodzących. Każdego interfejsu wychodzącego może być implementowana przez klienta do obiektu (ujścia). Aby uzyskać więcej informacji, zobacz [punkty połączenia ATL](../atl/atl-connection-points.md).

**Aby zaimplementować punktu połączenia:**

1. W widoku klas kliknij prawym przyciskiem myszy nazwę klasy dla obiektu ATL.

1. Wybierz **Dodaj** z menu skrótów, a następnie wybierz **Dodaj punkt połączenia** do wyświetlenia [Kreator implementacji punktu połączenia](#implement-connection-point-wizard).

1. Wybierz interfejsy punktu połączenia w celu wdrożenia z bibliotek odpowiedniego typu, a następnie wybierz pozycję **Zakończ**.

1. W widoku klas należy zbadać klasy serwera proxy, utworzone dla każdego punktu połączenia. Klasy są traktowane jako CProxy*InterfaceName*\<T > i są uzyskiwane z [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).

1. Kliknij dwukrotnie klasy punktów połączenia do wyświetlenia definicję klasy punktu połączenia.

   - W przypadku zaimplementowania punktu połączenia dla interfejsu własny projekt, pojawi się następujące definicje:

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - W przypadku zaimplementowania interfejsu lokalnego metody i właściwości są wyświetlane w treści klasy.

   - W przypadku zaimplementowania punktu połączenia dla innego interfejsu definicja zawiera metod tego interfejsu, każdy poprzedzone `Fire_`.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator implementacji punktu połączenia](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>Kreator implementacji punktu połączenia

Ten kreator implementuje punkt połączenia dla obiektów COM. Obiekt łączności (źródła) można wyświetlić punkt połączenia dla swoich własnych interfejsów lub dowolnego interfejsu wychodzącego. Visual C++ Windows zarówno i zapewniają bibliotek typów, które mają wychodzących interfejsów. Każdego interfejsu wychodzącego może być implementowana przez klienta do obiektu (ujścia).

Aby uzyskać więcej informacji, zobacz [punkty połączenia ATL](../atl/atl-connection-points.md).

- **Biblioteki typów dostępne**

  Wyświetla bibliotek dostępnych typów zawierający definicje interfejsu, dla których można wdrożyć punktów połączenia. Wybierz przycisk wielokropka, aby zlokalizować plik z biblioteki typów do użycia.

- **Lokalizacja**

  Wyświetla lokalizację biblioteki typów, aktualnie wybrane w **bibliotek typów dostępnych** listy.

- **Interfejsy**

  Wyświetla interfejsy, których definicje są przechowywane w bibliotece typów aktualnie wybrany w **bibliotek typów dostępnych** pole.

  |Przycisk transferu|Opis|
  |---------------------|-----------------|
  |**>**|Dodaje do **zaimplementować punkty połączenia** Nazwa interfejsu, aktualnie wybrane w listy **interfejsów** listy.|
  |**>>**|Dodaje do **zaimplementować punkty połączenia** listy dostępny w wszystkich nazw interfejsu **interfejsów** listy.|
  |**\<**|Usuwa nazwę interfejsu aktualnie wybrany w **zaimplementować punkty połączenia** listy.|
  |**\<\<**|Usuwa wszystkie interfejsu nazwy obecnie wymienione w **zaimplementować punkty połączenia** listy.|

- **Implementowanie punkty połączenia**

  Wyświetla nazwy interfejsów, które można zaimplementować punkty połączenia po wybraniu **Zakończ**.
