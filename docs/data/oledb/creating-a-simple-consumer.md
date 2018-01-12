---
title: Tworzenie prostego konsumenta | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5febdc019f5e575f685e4e93c892b7f5e777b776
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-simple-consumer"></a>Tworzenie prostego konsumenta
Służy Kreator projektu ATL i OLE DB Kreator konsumenta ATL do generowania konsumenta szablony OLE DB.  
  
#### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Aby utworzyć aplikację konsoli dla konsumentów OLE DB  
  
1.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  W okienku typów projektów kliknij **projekty Visual C++** folder, a następnie kliknij przycisk **projektu Win32** ikonę w okienku szablonów. W **nazwa** wprowadź nazwę projektu, na przykład **MyCons**.  
  
3.  Kliknij przycisk **OK**.  
  
     Zostanie wyświetlony Kreator projektu Win32.  
  
4.  Na **ustawienia aplikacji** wybierz pozycję **aplikacja Konsolowa**, a następnie wybierz **Dodaj obsługę ATL**.  
  
5.  Kliknij przycisk **Zakończ** aby zamknąć kreatora i generowania projektu.  
  
 Następnie użyj OLE DB Kreator konsumenta ATL, aby dodać obiekt konsumenta OLE DB.  
  
#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Aby utworzyć z klientem za pomocą OLE DB Kreator konsumenta ATL  
  
1.  W widoku klas, kliknij prawym przyciskiem myszy `MyCons` projektu.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
     **Dodaj klasę** zostanie wyświetlone okno dialogowe.  
  
3.  W okienku kategorii kliknij **Visual C++**, kliknij przycisk **OLE DB konsumenta ATL** ikony w okienku szablonów, a następnie kliknij przycisk **Otwórz**.  
  
     OLE DB Kreator konsumenta ATL zostanie wyświetlone.  
  
4.  Kliknij przycisk **źródła danych** przycisku.  
  
     **Właściwości Linku danych** zostanie wyświetlone okno dialogowe.  
  
5.  W **właściwości Linku danych** okna dialogowego pole, wykonaj następujące czynności:  
  
    -   Na **dostawcy** karcie, określ dostawcę OLE DB.  
  
    -   Na **połączenia** karcie, określ nazwę serwera, identyfikator logowania i hasło dla źródła danych i bazy danych na serwerze.  
  
    > [!NOTE]
    >  Istnieje problem z **Zezwalaj na zapisywanie haseł** funkcji **właściwości Linku danych** okno dialogowe. W **wprowadź informacje do logowania się do serwera**, dostępne są dwa przyciski radiowe: **zabezpieczenia zintegrowane systemu Windows NT użyj** i **Użyj określonej nazwy użytkownika i hasła**.  
  
    > [!NOTE]
    >  W przypadku wybrania **Użyj określonej nazwy użytkownika i hasła**, ma możliwość zapisania hasło (przy użyciu **Zezwalaj na zapisywanie haseł** pole wyboru), jednak ta opcja nie jest bezpieczne. Zaleca się, że wybrano **zabezpieczenia zintegrowane systemu Windows NT użyj**; ta opcja używa systemu Windows NT, aby zweryfikować swoją tożsamość.  
  
    > [!NOTE]
    >  Jeśli nie możesz użyć zabezpieczenia zintegrowane systemu Windows NT, należy użyć aplikacji warstwy środkowej monitowanie użytkownika o podanie hasła lub do przechowywania hasła w miejscu z mechanizmy zabezpieczeń, aby go lepiej chronić (a nie w kodzie źródłowym).  
  
     Po wybraniu dostawcy i inne ustawienia, kliknij przycisk **Testuj połączenie** można zweryfikować wybrane na poprzedniej strony — okno dialogowe. Jeśli **wyniki** polu raporty `Test connection succeeded`, kliknij przycisk **OK** do utworzenia połączenia danych.  
  
     **Obiektu bazy danych wybierz** zostanie wyświetlone okno dialogowe.  
  
6.  Formant drzewa wybierz tabeli, widoku lub procedury składowanej. Na potrzeby tej procedury należy wybierać tabeli Produkty bazy danych Northwind.  
  
7.  Kliknij przycisk **OK**. Nastąpi powrót do OLE DB Kreator konsumenta ATL.  
  
8.  Kreator zakończy pracę nazwy dla `Class` i **pliku .h** na podstawie nazwy tabeli, widoku lub wybrania procedurę składowaną. Jeśli chcesz, możesz edytować te nazwy.  
  
9. Wyczyść **atrybutami** pole wyboru, aby Kreator tworzy przy użyciu kodu konsumenta [klasy szablonów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) zamiast domyślnej [atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
10. W obszarze **typu**, wybierz pozycję **polecenia**.  
  
     Kreator tworzy [CCommand](../../data/oledb/ccommand-class.md)— na podstawie użytkownika, w przypadku wybrania **polecenia** lub [CTable](../../data/oledb/ctable-class.md)— na podstawie użytkownika, w przypadku wybrania **tabeli**. Po wybrany obiekt nosi nazwę klasy tabeli lub polecenia, ale można edytować nazwy.  
  
11. W obszarze **Obsługa**, pozostaw **zmiany**, **Wstaw**, i **usunąć** zaznaczaj pól.  
  
     Wybierz **zmiany**, **Wstaw**, i **usunąć** pola wyboru, aby obsługiwać zmiana, wstawianie i usuwanie rekordów w zestawie wierszy, jeśli jest to wymagane. Aby uzyskać więcej informacji na temat zapisywania danych z danymi, przechowywanie, zobacz [aktualizowanie zestawów wierszy](../../data/oledb/updating-rowsets.md).  
  
12. Kliknij przycisk **Zakończ** można utworzyć użytkownika.  
  
 Kreator generuje klasę polecenie i klasy rekordu użytkownika, jak pokazano w [Consumer Wizard-Generated klasy](../../data/oledb/consumer-wizard-generated-classes.md). Klasy poleceń będzie mieć nazwę, wprowadzony w `Class` pola kreatora (w tym przypadku `CProducts`), i klasy rekordów użytkowników mają nazwy w postaci "*ClassName*metody dostępu" (w tym przypadku `CProductsAccessor`).  
  
> [!NOTE]
>  Kreator umieszcza Products.h następujący wiersz:  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  Ten wiersz uniemożliwia Kompilowanie aplikacji klienta i przypomina Sprawdź ciąg połączenia ustalony haseł. Po sprawdzeniu parametrów połączenia, należy usunąć ten wiersz kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)