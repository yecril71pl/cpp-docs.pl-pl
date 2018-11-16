---
title: Implementowanie interfejsu
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 8e166f806d247cd93ff0f471360d749fa95e430b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692904"
---
# <a name="implement-an-interface"></a>Implementowanie interfejsu

Aby zaimplementować interfejs, musi utworzono projekt jako aplikację ATL COM lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

Po utworzeniu projektu, aby zaimplementować interfejs, należy najpierw dodać obiektu ATL. Zobacz [dodawać obiekty i kontrolki do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) listę kreatorzy dodawania obiektów do projektu ATL.

> [!NOTE]
> Kreator nie obsługuje okno dialogowe ATL, usługi XML sieci Web przy użyciu biblioteki ATL, obiekty wydajności i liczników wydajności.

Jeśli użytkownik [Dodawanie kontrolki ATL](../atl/reference/adding-an-atl-control.md), można określić, czy do implementacji interfejsów domyślne. Interfejsy domyślne są wymienione w [interfejsów](../atl/reference/interfaces-atl-control-wizard.md) stronie oznacza pracę kreatora i zdefiniowaną w atlcom.h.

Po dodaniu obiektu lub formantu, można zaimplementować innych interfejsów znajduje się w dowolnej bibliotece dostępnych typów za pomocą Kreatora implementacji interfejsu.

W przypadku dodawania nowego interfejsu, należy go ręcznie dodać do pliku .idl projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowego interfejsu w projekcie ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).

**Aby zaimplementować interfejs:**

1. W widoku klas kliknij prawym przyciskiem myszy nazwę klasy dla obiektu ATL.

1. Wybierz **Dodaj** z menu skrótów, a następnie wybierz **implementować interfejs** do wyświetlenia [Kreator implementowania interfejsu](#implement-interface-wizard).

1. Wybierz interfejsy do implementacji z bibliotek odpowiedniego typu, a następnie wybierz pozycję **Zakończ**.

1. W widoku klas, rozwiń węzeł bazy obiektu i języka node interfejsów, aby wyświetlić interfejs zastało zaimplementowane. Następnie rozwiń węzeł interfejsu, aby wyświetlić jego dostępnych właściwości, metody i zdarzenia.

   > [!NOTE]
   > Można również użyć [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code) zbadanie składowych interfejsu.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator implementacji interfejsu](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu

Ten kreator implementuje interfejs dla obiektu COM. Implementacje wiele interfejsów są objęte biblioteki COM, dostępna z poziomu programu Visual Studio i Windows. Implementacja interfejsu jest skojarzony z obiektem, gdy tworzone jest wystąpienie tego obiektu. Umożliwia także usług oferowanych przez obiekt.

Omówienie interfejsów i implementacji, zobacz [interfejsów i implementacje interfejsu](/windows/desktop/com/interfaces-and-interface-implementations) w zestawie Windows SDK.

- **Implementuj interfejs z**

  Określa lokalizację biblioteki typów, z którego jest tworzony interfejs.

  |Opcja|Opis|
  |------------|-----------------|
  |**Project**|Biblioteka typów jest częścią projektu.|
  |**Registry**|Biblioteka typów jest zarejestrowany w systemie. Zarejestrowanego typu biblioteki są wymienione w **bibliotek typów dostępnych**.|
  |**Plik**|Biblioteka typów musi być zarejestrowane w systemie, ale są przechowywane w pliku. Podaj lokalizację plików w programie **lokalizacji**.|

- **Biblioteki typów dostępne**

  Wyświetla bibliotek dostępnych typów zawierający definicje interfejsu, które można zaimplementować. Jeśli wybierzesz **pliku** w obszarze **implementuj interfejs z**, to pole jest niedostępna w przypadku zmiany.

- **Lokalizacja**

  Wyświetla lokalizację biblioteki typów, aktualnie wybrane w **bibliotek typów dostępnych** listy. W przypadku wybrania **pliku** w obszarze **implementuj interfejs z**, wybierz przycisk wielokropka, aby zlokalizować pliku zawierającego bibliotekę typów, aby użyć.

- **Interfejsy**

  Wyświetla interfejsy, których definicje są przechowywane w bibliotece typów aktualnie wybrany w **bibliotek typów dostępnych** pole.

  > [!NOTE]
  > Interfejsy, które mają taką samą nazwę jak już wdrożone przez wybrany obiekt nie są wyświetlane w **interfejsów** pole.

  |Przycisk transferu|Opis|
  |---------------------|-----------------|
  |**>**|Dodaje do **implementować interfejsy** Nazwa interfejsu, aktualnie wybrane w listy **interfejsów** listy.|
  |**>>**|Dodaje do **implementować interfejsy** listy dostępny w wszystkich nazw interfejsu **interfejsów** listy.|
  |**\<**|Usuwa nazwę interfejsu aktualnie wybrany w **implementować interfejsy** listy.|
  |**\<\<**|Usuwa wszystkie interfejsu nazwy obecnie wymienione w **implementować interfejsy** listy.|

- **Implementowanie interfejsów**

  Wyświetla nazwy interfejsów, które zostały wybrane do wdrożenia na obiekcie.

  > [!NOTE]
  > Jeśli dołączysz więcej niż jeden interfejs, który pochodzi od klasy `IDispatch`, lub jeśli użytkownik próbuje zaimplementować interfejs, który jest tworzony na podstawie innego interfejsu już w swojej klasie, a następnie muszą rozróżniać wpisy COM_MAP. Aby uzyskać więcej informacji, zobacz [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2).
