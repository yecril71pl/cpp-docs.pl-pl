---
title: Tworzenie prostego konsumenta
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: cc24df1f15d43c384e6bf3853766fad82cf51255
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707716"
---
# <a name="creating-a-simple-consumer"></a>Tworzenie prostego konsumenta

::: moniker range="vs-2019"

Kreator OLE DB konsumenta ATL nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [tworzenie konsumenta bez przy użyciu kreatora](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Użyj **Kreator projektów ATL** i **OLE DB Kreator konsumenta ATL** do generowania konsumenta szablony OLE DB.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Aby utworzyć aplikację konsolową w języku dla konsumenta OLE DB

1. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.

   **Nowy projekt** pojawi się okno dialogowe.

1. W **typów projektów** okienku kliknij **zainstalowane** > **Visual C++** > **pulpitu Windows** folderu a następnie kliknij przycisk **kreatora pulpitu Windows** ikonę **szablony** okienka. W **nazwa** wprowadź nazwę projektu, na przykład *MyCons*.

1. Kliknij przycisk **OK**.

   **Projektu pulpitu Windows** pojawi się Kreator.

1. Na **ustawienia aplikacji** wybierz opcję **aplikacji konsolowej programu**, a następnie wybierz pozycję **Dodaj wspólne nagłówki dla biblioteki ATL**.

1. Kliknij przycisk **OK** aby zamknąć kreatora i generowania projektu.

Następnie użyj **OLE DB Kreator konsumenta ATL** Aby dodać obiekt konsumenta OLE DB.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Aby utworzyć odbiorcę z OLE DB Kreator konsumenta ATL

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `MyCons` projektu.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **nowy element**.

   **Dodaj nowy element** pojawi się okno dialogowe.

1. W **kategorie** okienku kliknij **zainstalowane** > **Visual C++**  > **ATL**, kliknij przycisk  **Konsumenta OLE DB ATL** ikonę **szablony** okienku, a następnie kliknij przycisk **Dodaj**.

   **Kreator konsumenta OLE DB ATL** pojawia się.

1. Kliknij przycisk **źródła danych** przycisku.

   **Właściwości Linku danych** pojawi się okno dialogowe.

1. W **właściwości Linku danych** okna dialogowego pole, wykonaj następujące czynności:

   1. Na **dostawcy** karcie, określ dostawcę OLE DB.

   1. Na **połączenia** kartę, należy określić wymagane informacje, takie jak nazwa serwera, identyfikator logowania i hasło dla źródła danych i bazy danych na serwerze.

      > [!NOTE]
      > Występuje problem z zabezpieczeniami z **Zezwalaj na zapisywanie hasła** funkcji **właściwości Linku danych** okno dialogowe. W **wprowadź informacje, aby zalogować się do serwera**, istnieją dwa przyciski radiowe: **Użyj Windows NT zintegrowane zabezpieczenia** i **Użyj określonej nazwy użytkownika i hasła**.

      > [!NOTE]
      > Jeśli wybierzesz **Użyj określonej nazwy użytkownika i hasła**, masz możliwość zapisania hasła (przy użyciu **Zezwalaj na zapisywanie hasła** pole wyboru); Jednakże, ta opcja nie jest bezpieczne. Zaleca się, że wybrano **Użyj Windows NT zintegrowane zabezpieczenia**; ta opcja używa systemu Windows NT, aby zweryfikować swoją tożsamość.

      > [!NOTE]
      > Jeśli nie mogą używać zabezpieczeń zintegrowanych w systemu Windows NT, należy użyć aplikacji warstwy środkowej monitować użytkownika o podanie hasła lub hasło są przechowywane w lokalizacji za pomocą mechanizmów zabezpieczeń, aby go lepiej chronić (a nie w kodzie źródłowym).

   1. Po wybraniu dostawcy i inne ustawienia, kliknij przycisk **Testuj połączenie** Aby zweryfikować wybranych na stronach poprzednie okno dialogowe. Jeśli **wyniki** polu raporty `Test connection succeeded`, kliknij przycisk **OK** do utworzenia linku danych.

   **Obiektu bazy danych wybierz** pojawi się okno dialogowe.

1. Użyj kontrolki drzewa, aby wybrać tabeli, widoku lub procedury składowanej. W tym przykładzie wybierz `Products` tabeli `Northwind` bazy danych.

1. Kliknij przycisk **OK**. Nastąpi powrót do **OLE DB Kreator konsumenta ATL**.

1. Kreator zakończy pracę nazwy `Class` i **plik .h klasy** na podstawie nazwy tabeli, widoku lub przechowywane procedury, które wybrano. Jeśli chcesz, możesz edytować te nazwy.

1. Wyczyść **atrybutami** pole wyboru, aby Kreator tworzy kod konsumenta za pomocą [klasy szablonów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) zamiast domyślnego [atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md).

1. W obszarze **typu**, wybierz opcję **polecenia**.

   Kreator utworzy [CCommand](../../data/oledb/ccommand-class.md)— na podstawie konsumenta, jeśli zostanie wybrana **polecenia** lub [CTable](../../data/oledb/ctable-class.md)— na podstawie konsumenta, jeśli zostanie wybrana **tabeli**. Klasa tabeli lub polecenia jest nazwana na wybrany obiekt, ale można edytować nazwę.

1. W obszarze **pomocy technicznej**, pozostaw **zmiany**, **Wstaw**, i **Usuń** żadnych pól.

   Wybierz **zmiany**, **Wstaw**, i **Usuń** pola wyboru, aby obsługiwać zmiany, wstawianie i usuwanie rekordów w zestawie wierszy. Aby uzyskać więcej informacji na temat zapisywania danych do danych przechowywania, zobacz [aktualizowanie zestawów wierszy](../../data/oledb/updating-rowsets.md).

1. Kliknij przycisk **Zakończ** utworzyć konsumenta.

Kreator wygeneruje klasę polecenie i klasy rekordów użytkowników, jak pokazano w [klasy Consumer Wizard-Generated](../../data/oledb/consumer-wizard-generated-classes.md). Klasy poleceń będzie mieć nazwę, które wprowadziłeś w `Class` polu w Kreatorze (w tym przypadku `CProducts`), a klasa rekordu użytkownika będzie zawierał nazwę w postaci "*ClassName*metody dostępu" (w tym przypadku `CProductsAccessor`).

> [!NOTE]
> Kreator umieszcza następujący wiersz do `Products.h`:

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Ten wiersz zapobiega Kompilowanie aplikacji klienta i przypomina o tym, aby sprawdzić parametry połączenia dla zakodowanych hasła. Po sprawdzeniu parametry połączenia, możesz usunąć ten wiersz kodu.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
