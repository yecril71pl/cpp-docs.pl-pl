---
title: Obsługa bazy danych, kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: a1e0519e1351a48bbd969168d62f163c9dde7e7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323118"
---
# <a name="database-support-mfc-application-wizard"></a>Obsługa bazy danych, kreator aplikacji MFC

Ta strona zawiera opcje, które pozwalają na określenie poziomu bazy danych obsługują (plus ze źródłem danych, w razie potrzeby) dla Twojego projektu.

- **Obsługa bazy danych**

   Ustawia poziom obsługi bazy danych dla projektu.

   |Opcja|Opis|
   |------------|-----------------|
   |**Brak**|Nie obsługuje bazy danych. Jest to opcja domyślna.|
   |**Tylko pliki nagłówka**|Zapewnia podstawowy poziom obsługi bazy danych dla aplikacji. Jeśli zostanie wybrana pomoc techniczną ODBC, w ramach **typ klienta**, Kreator aplikacji MFC obejmuje do projektu plik nagłówkowy AFXDB. H. Dodaje bibliotek DLL, ale nie tworzy żadnych klasy specyficzne dla bazy danych. Możesz później utworzyć zestawy rekordów i używać ich do badania i aktualizowania rekordów. Jeśli zostanie wybrana pomoc techniczną OLE DB, w ramach **typ klienta**, dołączono następujące pliki nagłówków: ATLBASE. H AFXOLEDB. H ATLPLUS. GODZ.|
   |**Widok bazy danych bez obsługi plików**|Zawiera pliki nagłówkowe bazy danych, bibliotek DLL, widoku rekordu i zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **Obsługa architektury dokument/widok** opcji wybranej w [typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) strony.) Ta opcja powoduje dołączenie Obsługa dokumentów, ale nie obsługuje serializacji. Jeśli zdecydujesz się zawierały widok bazy danych, należy określić źródło danych.|
   |**Widok bazy danych z obsługą plików**|Zawiera pliki nagłówkowe bazy danych, bibliotek DLL, widoku rekordu i zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **Obsługa architektury dokument/widok** opcji wybranej w **typ aplikacji** strony.) Ta opcja obsługuje serializacja dokumentu, który umożliwia, na przykład, można zaktualizować pliku profilu użytkownika. Aplikacje baz danych są zazwyczaj działają na podstawie każdego rekordu, a nie na pliku podstawy i dlatego nie ma potrzeby serializacji. Mogą jednak mieć specjalne użycia serializacji. Jeśli zdecydujesz się zawierały widok bazy danych, należy określić źródło danych.|

   > [!NOTE]
   > W obszarze **baza danych obsługuje**, jeśli zostanie wybrana **OK bez obsługi plików bazy danych** lub **bazy danych widoku z obsługą plików**, pochodnym klasy widoku jest inny, zależności na Twojej **typ klienta** zaznaczenia w następujący sposób:

   - Jeśli wybierzesz **ODBC** w obszarze **typ klienta**, wówczas klasa widoku aplikacji pochodzi z [CRecordView](../../mfc/reference/crecordview-class.md). Ta klasa jest skojarzony z [CRecordset](../../mfc/reference/crecordset-class.md)-pochodne klasy, która Kreator aplikacji MFC tworzy również dla Ciebie. Ta opcja zapewnia oparte na formularzach aplikacji, w którym widoku rekordu służy do wyświetlania i aktualizowania rekordów za pomocą jego zestawu rekordów.

   - Jeśli wybierzesz **OLE DB** w obszarze **typ klienta**, a następnie Wyświetl klasę pochodną [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), i jest skojarzona z [CTable](../../data/oledb/ctable-class.md) lub [CCommand](../../data/oledb/ccommand-class.md)-klasy pochodnej.

- **Typ klienta**

   Wskazuje, czy projekt korzysta z klasy OLE DB lub ODBC.

   |Opcja|Opis|
   |------------|-----------------|
   |**OLE DB**|Gdy ta opcja jest zaznaczona, klikając **źródła danych** wywołuje przycisk **właściwości Linku danych** kreatora na pomocne podczas tworzenia połączenia ze źródłem danych OLE DB.|
   |**ODBC**|Gdy ta opcja jest zaznaczona, klikając **źródła danych** wywołuje przycisk **wybierz źródło danych** kreatora na pomocne podczas tworzenia połączenia ze źródłem danych ODBC.|

- **Źródło danych**

   Kliknij przycisk **źródła danych** przycisk, aby skonfigurować źródło danych przy użyciu określonego sterownika lub dostawcą a bazą danych. W przypadku wybrania OLE DB w **typ klienta** opcja, ten przycisk, wyświetla **właściwości Linku danych** okno dialogowe. W przypadku wybrania ODBC w **typ klienta** opcji i zawiera ten przycisk **wybierz źródło danych** okno dialogowe. Ta opcja jest dostępna tylko wtedy, gdy chcesz umieścić widok bazy danych w aplikacji.

   |Opcja|Opis|
   |------------|-----------------|
   |**Właściwości łącza danych** (OLE DB)|Ustanawia określonym źródłem danych przy użyciu określonego dostawcy OLE DB. Należy określić dostawcę OLE DB, lokalizacja danych, źródła danych, identyfikator logowania i (opcjonalnie) hasło. Aby uzyskać szczegółowe informacje dotyczące tego okna dialogowego, zobacz **źródła danych** w [OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Wybierz źródło danych** (ODBC)|Ustanawia określonym źródłem danych przy użyciu podanego sterownika ODBC. Należy wybrać nazwę źródła danych, aby wybrać tabelę dla źródła danych. Kreator wiąże wszystkie kolumny w tabeli zmienne Członkowskie `CRecordset`-klasy pochodnej. Aby uzyskać szczegółowe informacje dotyczące tego okna dialogowego, zobacz **źródła danych** w [Kreator użytkownika interfejsu ODBC MFC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

   > [!NOTE]
   > W poprzednich wersjach klawiszem Shift **źródła danych** przycisk otwarte okno dialogowe Otwieranie pliku pozwalają na wybór pliku połączenia danych (udl). Ta funkcja nie jest już obsługiwana.

- **Wygenerowana klasa opartego na atrybutach bazy danych**

   Dostępne tylko klienta OLE DB. Określa, czy klas baz danych w projekcie wygenerowanego używać atrybutów.

- **Powiąż wszystkie kolumny**

   Dostępne dla tylko klient ODBC. Określa, czy wszystkie kolumny w tabeli są powiązane. Jeśli zaznaczysz to pole, wszystkie kolumny są powiązane; Jeśli to pole nie jest zaznaczone, są powiązane żadne kolumny i musisz powiązać je ręcznie w klasie zestawu rekordów.

- **Typ**

   Dostępne dla tylko klient ODBC. Określa, czy zestaw rekordów jest dynamiczny lub migawki, zgodnie z opisem w poniższej tabeli.

   |Opcja|Opis|
   |------------|-----------------|
   |**Zestaw dynamiczny**|Określa, czy zestaw rekordów jest dynamiczny. Dynamiczny jest wynikiem kwerendę, która zawiera widok indeksowany do kwerendy bazy danych. Dynamiczny przechowuje tylko całkowitą indeksu do oryginalnych danych i związku z tym jest wydajność uzyskiwać za pośrednictwem migawki. Punkty indeksu bezpośrednio do każdego wybranego rekordu można odnaleźć wyniku zapytania i wskazuje, gdy rekord zostanie usunięty. Masz również dostęp do aktualnych informacji w rekordach kwerendy.|
   |**Migawka**|Określa, czy zestaw rekordów jest migawką. Migawka jest rezultat zapytania i wgląd w bazę danych w jednym punkcie w czasie. Wszystkie rekordy, które można odnaleźć wyniku kwerendy są buforowane, więc nie widzisz wszelkie zmiany, oryginalnym rekordów.|

## <a name="see-also"></a>Zobacz także

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)
