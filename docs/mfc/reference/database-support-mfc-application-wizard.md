---
title: Obsługa bazy danych, kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: c13d56d2fee45e130aba81168188bec6d8828d51
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365877"
---
# <a name="database-support-mfc-application-wizard"></a>Obsługa bazy danych, kreator aplikacji MFC

Ta strona zawiera opcje, które umożliwiają określenie poziomu obsługi bazy danych (plus źródło danych, jeśli to konieczne) dla projektu.

- **Obsługa bazy danych**

   Ustawia poziom obsługi bazy danych dla projektu.

   |Opcja|Opis|
   |------------|-----------------|
   |**Brak**|Nie zapewnia obsługi bazy danych. Jest to domyślne ustawienie opcji.|
   |**Tylko pliki nagłówkowe**|Zapewnia podstawowy poziom obsługi bazy danych dla aplikacji. Jeśli wybierzesz obsługę ODBC w obszarze **Typ klienta,** Kreator aplikacji MFC zawiera w projekcie plik nagłówka AFXDB. H. Dodaje biblioteki łączy, ale nie tworzy żadnych klas specyficznych dla bazy danych. Zestawy rekordów można tworzyć później i używać ich do sprawdzania i aktualizowania rekordów. Jeśli w obszarze Typ **klienta**wybierzesz obsługę OLE DB, uwzględniono następujące pliki nagłówkowe: ATLBASE. H AFXOLEDB. H ATLPLUS. H|
   |**Widok bazy danych bez obsługi plików**|Zawiera pliki nagłówków bazy danych, biblioteki łączy, widok rekordów i zestaw rekordów. (Dostępne tylko dla aplikacji z wybraną opcją **obsługi architektury dokumentu/widoku** na stronie [Typ aplikacji).](../../mfc/reference/application-type-mfc-application-wizard.md) Ta opcja obejmuje obsługę dokumentów, ale nie obsługuje serializacji. Jeśli zdecydujesz się dołączyć widok bazy danych, należy określić źródło danych.|
   |**Widok bazy danych z obsługą plików**|Zawiera pliki nagłówków bazy danych, biblioteki łączy, widok rekordów i zestaw rekordów. (Dostępne tylko dla aplikacji z wybraną opcją **obsługi architektury dokumentu/widoku** na stronie **Typ aplikacji).** Ta opcja obsługuje serializację dokumentu, której można użyć na przykład do zaktualizowania pliku profilu użytkownika. Aplikacje bazy danych zazwyczaj działają na podstawie dla rekordu, a nie na podstawie dla pliku, a więc nie wymagają serializacji. Jednak może mieć specjalne zastosowanie do serializacji. Jeśli zdecydujesz się dołączyć widok bazy danych, należy określić źródło danych.|

   > [!NOTE]
   > W obszarze **Obsługa bazy danych**, jeśli wybierzesz widok bazy danych bez obsługi **plików** lub widok bazy danych z **obsługą plików,** wyprowadzenie klasy widoku różni się w zależności od wyboru **typu klienta** w następujący sposób:

  - Jeśli wybierzesz **ODBC** w obszarze **Typ klienta,** klasa widoku aplikacji pochodzi od [CRecordView](../../mfc/reference/crecordview-class.md). Ta klasa jest skojarzona z [klasą crecordset](../../mfc/reference/crecordset-class.md)-derived, którą Kreator aplikacji MFC tworzy również dla Ciebie. Ta opcja umożliwia aplikację opartą na formularzach, w której widok rekordów jest używany do wyświetlania i aktualizowania rekordów za pośrednictwem jego zestawu rekordów.

  - Jeśli wybierzesz **OLE DB** w obszarze **Typ klienta,** klasa widoku pochodzi od [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)i jest skojarzona z klasą pochodną [CTable](../../data/oledb/ctable-class.md) lub [CCommand.](../../data/oledb/ccommand-class.md)

- **Typ klienta**

   Wskazuje, czy projekt używa ole db lub ODBC klas.

   |Opcja|Opis|
   |------------|-----------------|
   |**OLE DB**|Gdy ta opcja jest zaznaczona, kliknięcie przycisku **Źródło danych** wywołuje **Kreatora właściwości łącza danych,** aby ułatwić utworzenie połączenia ze źródłem danych OLE DB.|
   |**ODBC**|Gdy ta opcja jest zaznaczona, kliknięcie przycisku **Źródło danych** wywołuje **kreatora Wybierz źródło danych,** aby ułatwić utworzenie połączenia ze źródłem danych ODBC.|

- **Źródło danych**

   > [!NOTE]
   > Kreator konsumenta bazy danych ATL OLE DB i kreatora konsumenta odbc firmy MFC nie są dostępne w programie Visual Studio 2019 i nowszych. Nadal można dodać funkcje ręcznie. Aby uzyskać więcej informacji, zobacz [Tworzenie konsumenta bez użycia kreatora](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

   Kliknij przycisk **Źródło danych,** aby skonfigurować źródło danych przy użyciu określonego sterownika lub dostawcy i bazy danych. Jeśli w opcji Typ **klienta** wybrano ole db, w tym przycisku zostanie wyświetlone okno **dialogowe Właściwości łącza danych.** Jeśli w opcji **Typ klienta** wybrano odbc, ten przycisk zawiera okno dialogowe **Wybieranie źródła danych.** Ta opcja jest dostępna tylko wtedy, gdy zdecydujesz się dołączyć widok bazy danych w aplikacji.

   |Opcja|Opis|
   |------------|-----------------|
   |**Właściwości łącza danych** (OLE DB)|Ustanawia określone źródło danych przy użyciu określonego dostawcy ole db. Należy określić dostawcę ole db, lokalizację danych, źródło danych, identyfikator logowania i (opcjonalnie) hasło. Aby uzyskać szczegółowe informacje na temat tego okna dialogowego, zobacz **Źródło danych** w [Kreatorze konsumenta BAZY DANYCH OLE DB .](../../atl/reference/atl-ole-db-consumer-wizard.md)|
   |**Wybierz źródło danych** (ODBC)|Ustanawia określone źródło danych przy użyciu określonego sterownika ODBC. Należy wybrać nazwę źródła danych, aby wybrać tabelę dla źródła danych. Kreator wiąże wszystkie kolumny tabeli ze zmiennymi elementami członkowskimi klasy pochodnej. `CRecordset` Aby uzyskać szczegółowe informacje na temat tego okna dialogowego, zobacz **Źródło danych** w [Kreatorze konsumenckim MFC ODBC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

- **Generowanie przypisanej klasy bazy danych**

   Dostępne tylko dla klienta OLE DB. Określa, czy klasy bazy danych w wygenerowanym projekcie używają atrybutów.

- **Powiąż wszystkie kolumny**

   Dostępne tylko dla klienta ODBC. Określa, czy wszystkie kolumny w wybranej tabeli są powiązane. Jeśli zaznaczysz to pole, wszystkie kolumny są powiązane; Jeśli to pole nie zostanie zaznaczone, żadne kolumny nie są powiązane i należy je powiązać ręcznie w klasie recordset.

- **Typ**

   Dostępne tylko dla klienta ODBC. Określa, czy zestaw rekordów jest zestawem dynaset czy migawką, zgodnie z opisem w poniższej tabeli.

   |Opcja|Opis|
   |------------|-----------------|
   |**Zestaw dynamiczny**|Określa, że zestaw rekordów jest zestawem dynaset. Dynaset jest wynikiem kwerendy, która udostępnia widok indeksowany do danych poszukiwanej bazy danych. Dynaset buforuje tylko integralną indeks do oryginalnych danych i w związku z tym oferuje przyrost wydajności w migawce. Indeks wskazuje bezpośrednio na każdy rekord znaleziony w wyniku kwerendy i wskazuje, czy rekord został usunięty. Masz również dostęp do zaktualizowanych informacji w poszukiwanych rekordach.|
   |**Migawka**|Określa, że znak rekordów jest migawką. Migawka jest wynikiem kwerendy i jest widok do bazy danych w jednym momencie w czasie. Wszystkie rekordy znalezione w wyniku kwerendy są buforowane, więc nie są widoczne żadne zmiany w oryginalnych rekordach.|

## <a name="see-also"></a>Zobacz też

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)
