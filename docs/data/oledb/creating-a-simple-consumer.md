---
title: Tworzenie prostego konsumenta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e9f7c5a51765e2ce29df503aeefa9f850b71b1d4
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339857"
---
# <a name="creating-a-simple-consumer"></a>Tworzenie prostego konsumenta
Użyj Kreatora projektów ATL i OLE DB Kreator konsumenta ATL do wygenerowania konsumenta szablony OLE DB.  
  
### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Aby utworzyć aplikację konsolową w języku dla konsumenta OLE DB  
  
1.  Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2.  W okienku typów projektów, kliknij przycisk **projekty języka Visual C++** folder, a następnie kliknij **projekt systemu Win32** ikonę w okienku szablonów. W **nazwa** wprowadź nazwę projektu, na przykład **MyCons**.  
  
3.  Kliknij przycisk **OK**.  
  
     Zostanie wyświetlony Kreator projektu Win32.  
  
4.  Na **ustawienia aplikacji** wybierz opcję **aplikacji konsolowej programu**, a następnie wybierz pozycję **Dodaj obsługę ATL**.  
  
5.  Kliknij przycisk **Zakończ** aby zamknąć kreatora i generowania projektu.  
  
 Następnie użyj OLE DB Kreator konsumenta ATL, aby dodać obiekt konsumenta OLE DB.  
  
#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Aby utworzyć odbiorcę z OLE DB Kreator konsumenta ATL  
  
1.  W widoku klas kliknij prawym przyciskiem myszy `MyCons` projektu.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
     **Dodaj klasę** pojawi się okno dialogowe.  
  
3.  W okienku kategorii kliknij **Visual C++**, kliknij przycisk **OLE DB konsumenta ATL** ikonę w okienku szablonów, a następnie kliknij **Otwórz**.  
  
     Zostanie wyświetlony Kreator biblioteki ATL OLE DB konsumenta.  
  
4.  Kliknij przycisk **źródła danych** przycisku.  
  
     **Właściwości Linku danych** pojawi się okno dialogowe.  
  
5.  W **właściwości Linku danych** okna dialogowego pole, wykonaj następujące czynności:  
  
    -   Na **dostawcy** karcie, określ dostawcę OLE DB.  
  
    -   Na **połączenia** karcie, określ nazwę serwera, identyfikator logowania i hasło dla źródła danych i bazy danych na serwerze.  
  
    > [!NOTE]
    >  Występuje problem z zabezpieczeniami z **Zezwalaj na zapisywanie hasła** funkcji **właściwości Linku danych** okno dialogowe. W **wprowadź informacje, aby zalogować się do serwera**, istnieją dwa przyciski radiowe: **Użyj Windows NT zintegrowane zabezpieczenia** i **Użyj określonej nazwy użytkownika i hasła**.  
  
    > [!NOTE]
    >  Jeśli wybierzesz **Użyj określonej nazwy użytkownika i hasła**, masz możliwość zapisania hasła (przy użyciu **Zezwalaj na zapisywanie hasła** pole wyboru); Jednakże, ta opcja nie jest bezpieczne. Zaleca się, że wybrano **Użyj Windows NT zintegrowane zabezpieczenia**; ta opcja używa systemu Windows NT, aby zweryfikować swoją tożsamość.  
  
    > [!NOTE]
    >  Jeśli nie mogą używać zabezpieczeń zintegrowanych w systemu Windows NT, należy użyć aplikacji warstwy środkowej monitować użytkownika o podanie hasła lub hasło są przechowywane w lokalizacji za pomocą mechanizmów zabezpieczeń, aby go lepiej chronić (a nie w kodzie źródłowym).  
  
     Po wybraniu dostawcy i inne ustawienia, kliknij przycisk **Testuj połączenie** Aby zweryfikować wybranych na stronach poprzednie okno dialogowe. Jeśli **wyniki** polu raporty `Test connection succeeded`, kliknij przycisk **OK** do utworzenia linku danych.  
  
     **Obiektu bazy danych wybierz** pojawi się okno dialogowe.  
  
6.  Użyj kontrolki drzewa, aby wybrać tabeli, widoku lub procedury składowanej. Na potrzeby tej procedury należy wybierać tabeli Produkty bazy danych Northwind.  
  
7.  Kliknij przycisk **OK**. Nastąpi powrót do ATL OLE DB konsumenta kreatora.  
  
8.  Kreator zakończy pracę nazwy `Class` i **plik .h klasy** na podstawie nazwy tabeli, widoku lub przechowywane procedury, które wybrano. Jeśli chcesz, możesz edytować te nazwy.  
  
9. Wyczyść **atrybutami** pole wyboru, aby Kreator tworzy kod konsumenta za pomocą [klasy szablonów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) zamiast domyślnego [atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
10. W obszarze **typu**, wybierz opcję **polecenia**.  
  
     Kreator utworzy [CCommand](../../data/oledb/ccommand-class.md)— na podstawie konsumenta, jeśli zostanie wybrana **polecenia** lub [CTable](../../data/oledb/ctable-class.md)— na podstawie konsumenta, jeśli zostanie wybrana **tabeli**. Klasa tabeli lub polecenia jest nazwana na wybrany obiekt, ale można edytować nazwę.  
  
11. W obszarze **pomocy technicznej**, pozostaw **zmiany**, **Wstaw**, i **Usuń** żadnych pól.  
  
     Wybierz **zmiany**, **Wstaw**, i **Usuń** pola wyboru, aby obsługiwać zmiany, wstawianie i usuwanie rekordów w zestawie wierszy, w razie potrzeby. Aby uzyskać więcej informacji na temat zapisywania danych do danych przechowywania, zobacz [aktualizowanie zestawów wierszy](../../data/oledb/updating-rowsets.md).  
  
12. Kliknij przycisk **Zakończ** utworzyć konsumenta.  
  
 Kreator wygeneruje klasę polecenie i klasy rekordów użytkowników, jak pokazano w [klasy Consumer Wizard-Generated](../../data/oledb/consumer-wizard-generated-classes.md). Klasy poleceń będzie mieć nazwę, które wprowadziłeś w `Class` polu w Kreatorze (w tym przypadku `CProducts`), a klasa rekordu użytkownika będzie zawierał nazwę w postaci "*ClassName*metody dostępu" (w tym przypadku `CProductsAccessor`).  
  
> [!NOTE]
>  Kreator umieszcza następujący wiersz w Products.h:  
  
```cpp  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  Ten wiersz zapobiega Kompilowanie aplikacji klienta i przypomina o tym, aby sprawdzić parametry połączenia dla zakodowanych hasła. Po sprawdzeniu parametry połączenia, możesz usunąć ten wiersz kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)