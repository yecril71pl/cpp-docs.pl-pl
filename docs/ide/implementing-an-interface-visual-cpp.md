---
title: Implementowanie interfejsu
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: bb1db35e269ef884f3ebdf4564d8f0a3e579db50
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509513"
---
# <a name="implement-an-interface"></a>Implementowanie interfejsu

Aby zaimplementować interfejs, należy utworzyć projekt jako aplikację ATL COM lub jako aplikację MFC, która zawiera obsługę ATL. Możesz użyć [Kreatora projektu ATL](../atl/reference/atl-project-wizard.md) do utworzenia aplikacji ATL lub [dodać obiekt ATL do aplikacji MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) w celu zaimplementowania obsługi ATL dla aplikacji MFC.

Po utworzeniu projektu, aby zaimplementować interfejs, należy najpierw dodać obiekt ATL. Zobacz [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) , aby wyświetlić listę kreatorów, które dodają obiekty do projektu ATL.

> [!NOTE]
> Kreator nie obsługuje okien dialogowych ATL, usług sieci Web XML przy użyciu ATL, obiektów wydajności ani liczników wydajności.

Jeśli [dodasz kontrolkę ATL](../atl/reference/adding-an-atl-control.md), możesz określić, czy zaimplementować interfejsy domyślne. Interfejsy domyślne są wyświetlane na stronie [interfejsy](../atl/reference/interfaces-atl-control-wizard.md) tego kreatora i zdefiniowane w atlcom. h.

Po dodaniu obiektu lub formantu można zaimplementować inne interfejsy, znajdujące się w dowolnej dostępnej bibliotece typów, za pomocą Kreatora implementacji interfejsu.

W przypadku dodawania nowego interfejsu należy dodać go ręcznie do pliku. idl projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowego interfejsu w projekcie ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).

**Aby zaimplementować interfejs:**

1. W Widok klasy kliknij prawym przyciskiem myszy nazwę klasy dla obiektu ATL.

1. Wybierz pozycję **Dodaj** z menu skrótów, a następnie wybierz polecenie **Implementuj interfejs** , aby wyświetlić [Kreatora Implementuj interfejs](#implement-interface-wizard).

1. Wybierz interfejsy do wdrożenia z odpowiednich bibliotek typów, a następnie wybierz pozycję **Zakończ**.

1. W Widok klasy rozwiń węzeł bazy i interfejsy obiektu, aby zobaczyć interfejs, który został zaimplementowany. Następnie rozwiń węzeł interfejsu, aby wyświetlić jego dostępne właściwości, metody i zdarzenia.

   > [!NOTE]
   > Możesz również użyć [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code) do sprawdzenia elementów członkowskich interfejsu.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator implementacji interfejsu](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu

Ten Kreator implementuje interfejs dla obiektu COM. Implementacje wielu interfejsów są zawarte w bibliotekach COM dostępnych w programie Visual Studio i Windows. Implementacja interfejsu jest skojarzona z obiektem po utworzeniu wystąpienia tego obiektu. Udostępnia również usługi, które oferuje obiekt.

Aby zapoznać się z omówieniem interfejsów i implementacji, zobacz [interfejsy i implementacje](/windows/win32/com/interfaces-and-interface-implementations) interfejsów w Windows SDK.

- **Implementuj interfejs z**

  Określa lokalizację biblioteki typów, z której tworzony jest interfejs.

  |Opcja|Opis|
  |------------|-----------------|
  |**Project**|Biblioteka typów jest częścią projektu.|
  |**Registry**|Biblioteka typów jest zarejestrowana w systemie. Zarejestrowane biblioteki typów są wymienione w **dostępnych bibliotekach typów**.|
  |**Plik**|Biblioteka typów nie musi być zarejestrowana w systemie, ale jest przechowywana w pliku. Podaj lokalizację pliku w **lokalizacji**.|

- **Dostępne biblioteki typów**

  Wyświetla dostępne biblioteki typów posiadające definicje interfejsów, które można zaimplementować. Jeśli wybierzesz opcję **plik** w obszarze **Implementuj interfejs z**, to pole jest niedostępne do zmiany.

- **Lokalizacja**

  Wyświetla lokalizację biblioteki typów aktualnie zaznaczonej na liście **dostępne biblioteki typów** . Jeśli wybrano opcję **plik** w obszarze **Implementuj interfejs z**, wybierz przycisk wielokropka, aby zlokalizować plik, który ma być używany z biblioteką typów.

- **Interfejsy**

  Wyświetla interfejsy, których definicje są przechowywane w bibliotece typów aktualnie zaznaczonej w polu **dostępne biblioteki typów** .

  > [!NOTE]
  > Interfejsy, które mają taką samą nazwę jak te, które są już zaimplementowane przez wybrany obiekt, nie są wyświetlane w polu **interfejsy** .

  |Przycisk transferu|Opis|
  |---------------------|-----------------|
  |**>**|Dodaje do listy **Implementuj interfejsy** , która jest aktualnie wybrana na liście **interfejsy** .|
  |**>>**|Dodaje do listy **Implementuj interfejsy** wszystkie nazwy interfejsów dostępne na liście **interfejsy** .|
  |**\<**|Usuwa nazwę interfejsu aktualnie wybraną z listy **Implementuj interfejsy** .|
  |**\<\<**|Usuwa wszystkie nazwy interfejsów aktualnie wymienione na liście **Implementuj interfejsy** .|

- **Implementuj interfejsy**

  Wyświetla nazwy interfejsów, które zostały wybrane do zaimplementowania w obiekcie.

  > [!NOTE]
  > Jeśli dołączysz więcej niż jeden interfejs, który `IDispatch`pochodzi z, lub jeśli spróbujesz zaimplementować interfejs pochodzący z innego interfejsu, który jest już w klasie, należy odróżnić wpisy COM_MAP. Aby uzyskać więcej informacji, zobacz [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2).
