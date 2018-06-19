---
title: Obsługa bazy danych, Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.database
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86c6cd679b69bf84504d6735ca39d572bd48ff07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372247"
---
# <a name="database-support-mfc-application-wizard"></a>Obsługa bazy danych, kreator aplikacji MFC
Ta strona zawiera opcje, które pozwalają określić poziom bazy danych obsługuje (oraz źródła danych, w razie potrzeby) dla projektu.  
  
 **Obsługa baz danych**  
 Ustawia poziom obsługi bazy danych dla projektu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Brak**|Nie zapewnia bazy danych obsługi. Jest to opcja domyślna.|  
|**Tylko pliki nagłówka**|Udostępnia podstawowy poziom obsługi bazy danych dla aplikacji. W przypadku wybrania Obsługa ODBC w obszarze **typ klienta**, Kreator aplikacji MFC zawiera w projekcie AFXDB plik nagłówka. H. Dodaje biblioteki dll, ale nie powoduje żadnych klasy specyficzne dla bazy danych. Można utworzyć później zestawów rekordów i używać ich do badania i aktualizowania rekordów. W przypadku wybrania Obsługa OLE DB w obszarze **typ klienta**, dołączane są następujące pliki nagłówka: ATLBASE. H AFXOLEDB. H ATLPLUS. H|  
|**Widok bazy danych bez obsługi plików**|Zawiera bazy danych, pliki nagłówkowe, biblioteki dll i widoku rekordu zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **wsparcie dla architektury dokument/widok** opcji wybranej w [typu aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) strony.) Ta opcja powoduje dołączenie Obsługa dokumentu, ale nie obsługuje serializacji. Jeśli wybierzesz obejmują widoku bazy danych, należy określić źródło danych.|  
|**Widok bazy danych z obsługą plików**|Zawiera bazy danych, pliki nagłówkowe, biblioteki dll i widoku rekordu zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **wsparcie dla architektury dokument/widok** opcji wybranej w **typu aplikacji** strony.) Ta opcja obsługuje serializacji dokument, którego użyjesz, na przykład, aby zaktualizować plik profilu użytkownika. Aplikacje baz danych są zazwyczaj działają na podstawie na rekordu, a nie na jeden plik podstawy i dlatego nie ma potrzeby serializacji. Mogą jednak mieć specjalne używany do serializacji. Jeśli wybierzesz obejmują widoku bazy danych, należy określić źródło danych.|  
  
> [!NOTE]
>  W obszarze **baza danych obsługuje**, jeśli zostanie wybrana **bazy danych widoku bez obsługi plików** lub **bazy danych widoku z obsługą plików**, widok pochodnym klasy różni się, w zależności w Twojej **typ klienta** zaznaczenia w następujący sposób:  
  
-   W przypadku wybrania **ODBC** w obszarze **typ klienta**, a następnie pochodną klasy widoku aplikacji [CRecordView](../../mfc/reference/crecordview-class.md). Ta klasa jest skojarzony z [crecordset —](../../mfc/reference/crecordset-class.md)-pochodzi z klasy, która tworzy także Kreator aplikacji MFC dla Ciebie. Ta opcja umożliwia opartych na formularzach aplikacji, w którym widoku rekordu jest używana do wyświetlania i aktualizowania rekordów za pośrednictwem jej zestawu rekordów.  
  
-   W przypadku wybrania **OLE DB** w obszarze **typ klienta**, a następnie pochodną klasy widoku [coledbrecordview —](../../mfc/reference/coledbrecordview-class.md), i jest ona skojarzona z [CTable](../../data/oledb/ctable-class.md) lub [CCommand](../../data/oledb/ccommand-class.md)-klasy.  
  
 **Typ klienta**  
 Wskazuje, czy projekt używa klasy OLE DB lub ODBC.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**OLE DB**|Gdy ta opcja jest zaznaczona, klikając pozycję **źródła danych** wywołuje przycisk **właściwości Linku danych** kreatora pozwala utworzyć połączenie ze źródłem danych OLE DB.|  
|**ODBC**|Gdy ta opcja jest zaznaczona, klikając pozycję **źródła danych** wywołuje przycisk **wybierz źródło danych** kreatora pozwala utworzyć połączenie ze źródłem danych ODBC.|  
  
 **Źródło danych**  
 Kliknij przycisk **źródła danych** przycisk, aby skonfigurować źródło danych przy użyciu podanego sterownika lub dostawcy i bazy danych. W przypadku wybrania OLE DB w **typ klienta** wyświetla ten przycisk opcji **właściwości Linku danych** okno dialogowe. W przypadku wybrania ODBC w **typ klienta** opcję zawiera ten przycisk **wybierz źródło danych** okno dialogowe. Ta opcja jest dostępna tylko wtedy, gdy użytkownik chce umieścić widoku bazy danych w aplikacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Właściwości łącza danych** (OLE DB)|Ustanawia z określonego źródła danych przy użyciu określonego dostawcy OLE DB. Należy określić dostawcę OLE DB, lokalizacji danych, źródła danych, identyfikator logowania i (opcjonalnie) hasła. Aby uzyskać szczegółowe informacje w tym oknie dialogowym, zobacz **źródła danych** w [OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|  
|**Wybierz źródło danych** (ODBC)|Ustanawia z określonego źródła danych przy użyciu podanego sterownika ODBC. Musisz wybrać nazwę źródła danych, aby wybrać tabelę dla źródła danych. Kreator wiąże wszystkie kolumny tabeli zmiennych `CRecordset`-klasy. Aby uzyskać szczegółowe informacje w tym oknie dialogowym, zobacz **źródła danych** w [Kreator konsumenta MFC ODBC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|  
  
> [!NOTE]
>  W poprzednich wersjach, klikając przycisk Shift **źródła danych** przycisk otworzyć okno dialogowe Otwieranie pliku pozwala wybrać pliku połączenia danych (udl). Ta funkcja nie jest już obsługiwana.  
  
 **Generuj klasy oparte na atrybutach bazy danych**  
 Dostępne tylko klienta OLE DB. Określa, czy klasy baz danych w projekcie wygenerowanego używać atrybutów.  
  
 **Powiąż wszystkich kolumn**  
 Dostępne tylko klienta ODBC. Określa, czy wszystkie kolumny w tabeli są powiązane. Jeśli zaznaczysz to pole wszystkie kolumny są powiązane; Jeśli to pole nie jest zaznaczone, Brak kolumn są powiązane i należy powiązać je ręcznie w klasie zestawu rekordów.  
  
 **Typ**  
 Dostępne tylko klienta ODBC. Określa, czy zestaw rekordów jest dynamiczny lub migawki, zgodnie z opisem w poniższej tabeli.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Zestaw dynamiczny**|Określa, czy zestaw rekordów jest dynamiczny. Zestaw dynamiczny jest wynikiem kwerendę, która udostępnia widok indeksowany w danych, którego dotyczy kwerenda bazy danych. Zestaw dynamiczny buforuje tylko integralną indeks do oryginalnych danych i w związku z tym uzyskanie oferty a wydajności za pośrednictwem migawki. Wskazuje indeks bezpośrednio każdego rekordu znaleziono wyniku zapytania i wskazuje, czy rekord jest usuwany. Masz również dostęp do aktualnych informacji w rekordach, którego dotyczy kwerenda.|  
|Migawka|Określa, czy zestaw rekordów jest to migawka. Migawka jest wynik zapytania i widoku do bazy danych w jednym punkcie w czasie. Wszystkie rekordy znaleziono wyniku zapytania są buforowane, dlatego nie ma zmiany w oryginalnym rekordów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)
