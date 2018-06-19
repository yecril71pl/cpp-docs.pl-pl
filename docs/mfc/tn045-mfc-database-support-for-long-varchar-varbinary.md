---
title: 'TN045: Obsługa bazy danych MFC Varchar — Varbinary | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.data
dev_langs:
- C++
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd5201661afcdf6f4ae9676323f3f644817bcf7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386083"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: obsługa MFC/bazy danych pod względem typu danych Varchar/Varbinary
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisano, jak pobrać i wysyłać ODBC **SQL_LONGVARCHAR** i **SQL_LONGVARBINARY** klasy bazy danych za pomocą MFC typów danych.  
  
## <a name="overview-of-long-varcharvarbinary-support"></a>Omówienie obsługi długo Varchar/Varbinary  
 ODBC **SQL_LONG_VARCHAR** i **SQL_LONGBINARY** typy danych (nazywane tutaj długo kolumny danych) może przechowywać dużych ilości danych. Istnieją 3 sposoby może obsługiwać te dane:  
  
-   Aby powiązać `CString` / `CByteArray`.  
  
-   Aby powiązać `CLongBinary`.  
  
-   Nie powiązać go na wszystkich i pobrać i wysłać wartość danych long ręcznie, niezależnie od klasy baz danych.  
  
 Każdy z trzech metod ma zalety i wady.  
  
 Kolumny danych LONG nie są obsługiwane dla parametrów do zapytania. Są obsługiwane dla outputColumns.  
  
## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Cstring — / CByteArray powiązanie kolumny danych Long  
 Zalety:  
  
 Takie podejście jest łatwy do zrozumienia i pracować z znanych klasy. Zapewnia platformę `CFormView` obsługę `CString` z `DDX_Text`. Masz wiele ogólne funkcje ciągu lub kolekcji z `CString` i `CByteArray` klasy, a można kontrolować ilość pamięci przydzielonej lokalnie do przechowywania wartości danych. Platformę zachowuje stary kopię danych pola podczas **Edytuj** lub `AddNew` wywołania funkcji i będzie można framework automatycznie wykryć zmiany danych.  
  
> [!NOTE]
>  Ponieważ `CString` jest przeznaczony do pracy w danych znakowych i `CByteArray` pracy danych binarnych, zalecane jest umieszczenie danych znakowych (**SQL_LONGVARCHAR**) do `CString`, a danych binarnych ( **SQL_LONGVARBINARY**) do `CByteArray`.  
  
 Funkcje RFX dla `CString` i `CByteArray` ma dodatkowy argument pozwalającej przesłonić domyślny rozmiar alokacji pamięci, aby pomieścić pobranej wartości dla kolumny. Uwaga argument nMaxLength w deklaracjach następujących funkcji:  
  
```  
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,  
    CString& value,
    int nMaxLength = 255,
    int nColumnType = 
    SQL_VARCHAR);

 
void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,   
    CByteArray& value,
    int nMaxLength = 255);
```  
  
 Po pobraniu danych long kolumny na `CString` lub `CByteArray`, zwróciła maksymalną ilość danych jest domyślnie 255 bajtów. Niczego poza tym jest ignorowana. W takim przypadku platformę zgłosi wyjątek **AFX_SQL_ERROR_DATA_TRUNCATED**. Na szczęście można jawnie zwiększyć nMaxLength większej wartości do **MAXINT**.  
  
> [!NOTE]
>  Wartość nMaxLength jest używane przez MFC można ustawić lokalnej bufor **SQLBindColumn** funkcji. To jest lokalne bufor dla magazynu danych i nie faktycznie wpływa na ilość danych zwróconych przez sterownik ODBC. `RFX_Text` i `RFX_Binary` tylko utworzyć wywołanie przy użyciu **SQLFetch** do pobierania danych z bazy danych zaplecza. Każdego sterownika ODBC obowiązuje ograniczenie różnych ilości danych, które zwracają w jednym pobierania. Ten limit, może być mniejsza niż wartość w polu nMaxLength, w tym przypadku wyjątek **AFX_SQL_ERROR_DATA_TRUNCATED** zostanie wygenerowany. W tych warunkach, przełącz się do przy użyciu `RFX_LongBinary` zamiast `RFX_Text` lub `RFX_Binary` , dzięki czemu można pobrać wszystkich danych.  
  
 Powiąże ClassWizard **SQL_LONGVARCHAR** do `CString`, lub **SQL_LONGVARBINARY** do `CByteArray` dla Ciebie. Jeśli chcesz przydzielić więcej niż 255 bajtów, w których można pobrać kolumny danych long, możesz podać jawną wartość dla nMaxLength.  
  
 Gdy kolumny dużo danych jest powiązany z `CString` lub `CByteArray`, aktualizowanie pola działa w taki sam jak kiedy jest on powiązany z SQL_**VARCHAR** lub SQL_**VARBINARY**. Podczas **Edytuj**, wartość danych jest buforowana optymalizacji i później w porównaniu po **aktualizacji** jest wywoływana, aby wykryć zmiany danych wartości i ustawić Dirty i odpowiednio Null wartości dla kolumny.  
  
## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Clongbinary — wiązanie kolumn danych Long  
 Jeśli kolumny danych long może zawierać więcej **MAXINT** bajtów danych, prawdopodobnie warto go do pobierania `CLongBinary`.  
  
 Zalety:  
  
 Pobiera to kolumnę danych long całego do dostępnej pamięci.  
  
 Wady:  
  
 Dane są przechowywane w pamięci. To podejście jest również zbyt duży dla bardzo dużych ilości danych. Należy wywołać `SetFieldDirty` dla powiązania danych elementu członkowskiego, aby upewnić się, w polu znajduje się w **aktualizacji** operacji.  
  
 Po pobraniu danych long kolumn do `CLongBinary`, klasy baz danych zostanie sprawdzić łączny rozmiar kolumny danych long, a następnie przydzielić `HGLOBAL` wystarczająco duży do przechowywania jego całą wartość segmentu pamięci. Klasy baz danych następnie pobrać wartości danych w przydzielony `HGLOBAL`.  
  
 Jeśli źródło danych nie może zwrócić oczekiwany rozmiar kolumny danych long, platformę zgłosi wyjątek **AFX_SQL_ERROR_SQL_NO_TOTAL**. Jeśli próba przydzielić `HGLOBAL` kończy się niepowodzeniem, standard pamięci wyjątku.  
  
 Powiąże ClassWizard **SQL_LONGVARCHAR** lub **SQL_LONGVARBINARY** do `CLongBinary` dla Ciebie. Wybierz `CLongBinary` jako typ zmiennej w oknie dialogowym Dodawanie zmiennej elementu członkowskiego. ClassWizard spowoduje dodanie `RFX_LongBinary` wywołanie Twojej `DoFieldExchange` połączenia i zwiększyć całkowitą liczbę pól powiązania.  
  
 Aby zaktualizować długo wartości kolumny danych, najpierw upewnij się, przydzielony `HGLOBAL` jest wystarczająco duży, aby pomieścić nowych danych przez wywołanie metody **:: Funkcja GlobalSize** na `m_hData` członkiem `CLongBinary`. Jeśli jest za mały, zwolnij `HGLOBAL` i przydziel jeden odpowiedni rozmiar. Następnie ustaw `m_dwDataLength` aby odzwierciedlić nowy rozmiar.  
  
 W przeciwnym razie, jeśli `m_dwDataLength` jest większy niż rozmiar danych chcesz zmienić, można zwolnić i ponowne przydzielenie `HGLOBAL`, lub pozostaw przydzielone. Upewnij się, że wskazuje liczbę bajtów faktycznie używana w `m_dwDataLength`.  
  
## <a name="how-updating-a-clongbinary-works"></a>Działa jak aktualizowanie clongbinary —  
 Nie jest konieczne zrozumieć sposób aktualizowania `CLongBinary` działa, ale mogą być przydatne na przykład dotyczące wysyłania danych long wartości ze źródłem danych, jeśli ta metoda trzeci, opisane poniżej.  
  
> [!NOTE]
>  Aby `CLongBinary` pola, które mają zostać uwzględnione w aktualizację, musisz jawnie wywołać `SetFieldDirty` dla pola. Jeśli wprowadzisz zmiany do pola, łącznie z ustawieniem dla niego wartość Null, należy wywołać `SetFieldDirty`. Musisz również wywołać `SetFieldNull`, z drugi parametr jest **FALSE**, aby zaznaczyć pole jako mający wartość.  
  
 Podczas aktualizowania `CLongBinary` pola klasy baz danych użycia przez ODBC **DATA_AT_EXEC** mechanizmu (zobacz dokumentację ODBC **SQLSetPos**w rgbValue argument). Gdy platformę przygotowuje instrukcji insert lub update zamiast wskazujący `HGLOBAL` zawierające dane, *adres* z `CLongBinary` jest ustawiony jako *wartość* kolumny Zamiast tego i wartość wskaźnika długość **SQL_DATA_AT_EXEC**. Później, gdy instrukcji update jest wysyłana do źródła danych **SQLExecDirect** zwróci **SQL_NEED_DATA**. Alerty platformę czy wartości parametrów dla tej kolumny jest rzeczywiście adres `CLongBinary`. Wywołania framework **Procedura SQLGetData** raz buforem małych, oczekiwano sterownik do zwrócenia z rzeczywistą długością danych. Jeśli sterownik zwraca rzeczywista długość dużego obiektu binarnego (BLOB), MFC ponownie tyle miejsca w razie potrzeby można pobrać obiektu BLOB. Jeśli źródło danych zwraca **SQL_NO_TOTAL**, wskazując, że nie można określić rozmiar obiektu BLOB, MFC utworzy mniejsze bloki. Początkowy rozmiar domyślny to 64 KB, a kolejne bloki będą podwaja rozmiar; na przykład drugi będzie 128 KB, trzecia jest 256 KB i tak dalej. Początkowy rozmiar jest konfigurowany.  
  
## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Powiązanie nie: Pobieranie/wysyłanie danych bezpośrednio z ODBC z Procedura SQLGetData  
 Przy użyciu tej metody należy całkowicie pominąć klasy baz danych i postępowania z kolumną danych long.  
  
 Zalety:  
  
 Może buforować dane na dysku w razie potrzeby, lub zdecydować dynamicznie ilość danych do pobrania.  
  
 Wady:  
  
 Nie pobieraj framework **Edytuj** lub `AddNew` pomocy technicznej, a musi być zapisana kod samodzielnie przeprowadzić podstawowe funkcje (**usunąć** działa, ponieważ nie jest to operacja poziomu kolumny).  
  
 W takim przypadku kolumny danych long musi znajdować się na liście wybierz zestawu rekordów, ale nie może być powiązane z przez platformę. Jednokierunkowej zrobić to podać własne instrukcji SQL za pomocą `GetDefaultSQL` lub jako lpszSQL argument `CRecordset`w **Otwórz** działać, a nie powiązać dodatkowe kolumny za pomocą wywołania funkcji RFX_. ODBC wymaga czy niezwiązanego pola są wyświetlane z prawej strony pola powiązane, dlatego dodanie urządzenia niepowiązanych kolumn lub kolumny na końcu listy wyboru.  
  
> [!NOTE]
>  Ponieważ kolumny danych long nie jest powiązany przez platformę, zmiany nie można obsłużyć z `CRecordset::Update` wywołania. Należy utworzyć i wysłać wymagane SQL **Wstaw** i **aktualizacji** instrukcje samodzielnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

