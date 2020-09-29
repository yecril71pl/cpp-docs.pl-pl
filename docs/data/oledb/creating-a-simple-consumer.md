---
title: Tworzenie prostego konsumenta
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: 0b142a73f66a796f3e22bae0aeacb88dc018aea9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501863"
---
# <a name="creating-a-simple-consumer"></a>Tworzenie prostego konsumenta

::: moniker range="vs-2019"

Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [Tworzenie klienta bez korzystania z Kreatora](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Aby wygenerować klienta szablonów OLE DB, użyj kreatora **projektu ATL** i Kreatora wieloskładnikowego **klienta ATL OLE DB** .

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Aby utworzyć aplikację konsolową dla OLE DB konsumenta

1. W menu **Plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **Projekt**.

   Zostanie wyświetlone okno dialogowe **Nowy projekt**.

1. W okienku **typy projektów** kliknij folder Visual C++ **zainstalowany**na  >  **Visual C++**  >  **pulpicie systemu Windows** , a następnie kliknij ikonę **Kreatora pulpitu systemu Windows** w okienku **Szablony** . W polu **Nazwa** wprowadź nazwę projektu, na *przykład.*

1. Kliknij przycisk **OK**.

   Zostanie wyświetlony Kreator **projektów klasycznych systemu Windows** .

1. Na stronie **Ustawienia aplikacji** wybierz pozycję **Aplikacja konsolowa**, a następnie wybierz pozycję **Dodaj wspólne pliki nagłówkowe dla biblioteki ATL**.

1. Kliknij przycisk **OK** , aby zamknąć kreatora i wygenerować projekt.

Następnie użyj **kreatora ATL OLE DB klienta** , aby dodać obiekt OLE DB konsumenta.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Aby utworzyć odbiorcę przy użyciu kreatora ATL OLE DB klienta

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy `MyCons` projekt.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

   Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

1. W okienku **Kategorie** kliknij pozycję **zainstalowane** > **Visual C++** > **ATL**, kliknij ikonę **użytkownika ATL OLEDB** w okienku **Szablony** , a następnie kliknij przycisk **Dodaj**.

   Zostanie wyświetlony **Kreator użytkownika ATL OLEDB** .

1. Kliknij przycisk **Źródło danych** .

   Zostanie wyświetlone okno dialogowe **Właściwości łącza danych** .

1. W oknie dialogowym **Właściwości łącza danych** wykonaj następujące czynności:

   1. Na karcie **dostawca** określ dostawcę OLE DB.

   1. Na karcie **połączenie** Określ wymagane informacje, takie jak nazwa serwera, identyfikator logowania i hasło dla źródła danych i bazy danych na serwerze.

      > [!NOTE]
      > Występuje problem z zabezpieczeniami z funkcją **Zezwalaj na zapisywanie hasła** okna dialogowego **Właściwości łącza danych** . W polu **Wprowadź informacje, aby zalogować się na serwerze**, istnieją dwa przyciski radiowe: **Użyj zintegrowanych zabezpieczeń systemu Windows NT** i **Użyj określonej nazwy użytkownika i hasła**.

      > [!NOTE]
      > W przypadku wybrania opcji **Użyj konkretnej nazwy użytkownika i hasła**można zapisać hasło (przy użyciu pola wyboru **Zezwalaj na zapisywanie hasła** ). Jednak ta opcja nie jest bezpieczna. Zalecane jest wybranie opcji **Użyj zintegrowanych zabezpieczeń systemu Windows NT**. Ta opcja powoduje użycie systemu Windows NT do zweryfikowania Twojej tożsamości.

      > [!NOTE]
      > Jeśli nie można użyć zintegrowanych zabezpieczeń systemu Windows NT, należy użyć aplikacji warstwy środkowej do wyświetlenia monitu o podanie hasła lub zapisania hasła w lokalizacji z mechanizmami zabezpieczeń, aby ułatwić ochronę (zamiast kodu źródłowego).

   1. Po wybraniu dostawcy i innych ustawień kliknij przycisk **Testuj połączenie** , aby sprawdzić wybory dokonane na poprzednich stronach okna dialogowego. Jeśli zostanie **Results** wyświetlone okno wyników `Test connection succeeded` , kliknij przycisk **OK** , aby utworzyć łącze danych.

   Zostanie wyświetlone okno dialogowe **Wybieranie obiektu bazy danych** .

1. Użyj kontrolki drzewo, aby wybrać tabelę, widok lub procedurę składowaną. Na potrzeby tego przykładu wybierz `Products` tabelę z `Northwind` bazy danych.

1. Kliknij przycisk **OK**. Spowoduje to powrót do **Kreatora użytkownika ATL OLE DB**.

1. Kreator uzupełnia nazwy `Class` **plików i. h** na podstawie nazwy wybranej tabeli, widoku lub procedury składowanej. Jeśli chcesz, możesz edytować te nazwy.

1. Wyczyść pole wyboru **atrybut** , aby Kreator tworzył kod konsumenta przy użyciu [OLE DB klas szablonów](../../data/oledb/ole-db-consumer-templates-reference.md) zamiast domyślnych [atrybutów konsumentów OLE DB](../../windows/attributes/ole-db-consumer-attributes.md).

1. W obszarze **Typ**wybierz **polecenie**.

   Kreator tworzy odbiorcę opartą na [CCommand](../../data/oledb/ccommand-class.md), jeśli wybrano opcję " **polecenie** " lub "konsument oparty na [CTable](../../data/oledb/ctable-class.md)", jeśli wybrano opcję **tabela**. Tabela lub Klasa poleceń jest nazywana po wybranym obiekcie, ale można edytować nazwę.

1. W obszarze **Pomoc techniczna**pozostaw usunięte pola **Zmień**, **Wstaw**i **Usuń** .

   Zaznacz pola wyboru **Zmień**, **Wstaw**i **Usuń** , aby obsłużyć zmiany, wstawianie i usuwanie rekordów w zestawie wierszy. Aby uzyskać więcej informacji na temat zapisywania danych w magazynie danych, zobacz [Aktualizowanie zestawów wierszy](../../data/oledb/updating-rowsets.md).

1. Kliknij przycisk **Zakończ** , aby utworzyć konsumenta.

Kreator generuje klasę poleceń i klasę rekordów użytkowników, jak pokazano w [klasach generowanych przez kreatora odbiorców](../../data/oledb/consumer-wizard-generated-classes.md). Klasa poleceń będzie miała nazwę wprowadzoną w `Class` polu Kreatora (w tym przypadku `CProducts` ), a Klasa rekordu użytkownika będzie miała nazwę "metoda dostępu*ClassName*" (w tym przypadku `CProductsAccessor` ).

> [!NOTE]
> Kreator umieści następujący wiersz w `Products.h` :

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Ten wiersz uniemożliwia skompilowanie aplikacji konsumenta i przypomina, aby sprawdzić parametry połączenia pod kątem zakodowanych haseł. Po sprawdzeniu parametrów połączenia można usunąć ten wiersz kodu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
