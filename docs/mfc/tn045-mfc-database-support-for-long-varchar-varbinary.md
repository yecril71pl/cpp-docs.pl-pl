---
title: 'TN045: Bazy danych MFC Obsługa Varchar-Varbinary | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 60869fbd450f6a2122c91b852c29222f7d4d0744
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436419"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: obsługa MFC/bazy danych pod względem typu danych Varchar/Varbinary

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje sposób pobierania i wysyłania ODBC **SQL_LONGVARCHAR** i **SQL_LONGVARBINARY** typy danych za pomocą MFC bazy danych klasy.

## <a name="overview-of-long-varcharvarbinary-support"></a>Omówienie obsługi długo Varchar/Varbinary

ODBC **SQL_LONG_VARCHAR** i **SQL_LONGBINARY** typy danych (określone tutaj jako długo kolumn danych) może przechowywać bardzo duże ilości danych. Istnieją 3 sposoby, które ułatwią Ci obsługę tych danych:

- Powiązać `CString` / `CByteArray`.

- Powiązać `CLongBinary`.

- Nie powiązać go na wszystkich pobierania i wysyłania wartość długo dane ręcznie, niezależnie od klas baz danych.

Każdy z trzech metod ma zalety i wady.

Kolumny długo dane nie są obsługiwane dla parametrów zapytania. Są one obsługiwane tylko dla outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Powiązanie kolumn danych Long CString/CByteArray

Zalety:

To podejście jest proste dowiedzieć się, a praca z klasami, znane. Udostępnia platformę `CFormView` Obsługa `CString` z `DDX_Text`. Zawiera wiele funkcji ogólne ciągu lub kolekcji przy użyciu `CString` i `CByteArray` klasy i możesz kontrolować ilość pamięci przydzielonej lokalnie w celu przechowywania wartości danych. Struktura zachowuje stary kopię danych pola podczas `Edit` lub `AddNew` wywołania funkcji i może framework automatycznie Wykryj zmiany danych dla Ciebie.

> [!NOTE]
>  Ponieważ `CString` jest przeznaczony do pracy nad danych znakowych i `CByteArray` nad dane binarne, zalecane jest umieszczenie danych znakowych (**SQL_LONGVARCHAR**) do `CString`i danych binarnych ( **SQL_LONGVARBINARY**) do `CByteArray`.

RFX funkcje dla `CString` i `CByteArray` ma dodatkowy argument, która pozwala zastąpić domyślny rozmiar alokacji pamięci na potrzeby przechowywania pobraną wartość dla kolumny. Należy zwrócić uwagę argumentu nMaxLength w poniższej deklaracji funkcji:

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

Jeśli pobieranie kolumn długich danych do `CString` lub `CByteArray`, maksymalną zwracana ilość danych jest domyślnie 255 bajtów. Niczego poza tym są ignorowane. W tym przypadku ramach spowoduje zgłoszenie wyjątku **AFX_SQL_ERROR_DATA_TRUNCATED**. Na szczęście możesz jawnie zwiększyć nMaxLength większe wartości do **MAXINT**.

> [!NOTE]
>  Wartość nMaxLength jest używane przez MFC można ustawić lokalnej bufor `SQLBindColumn` funkcji. To jest lokalne bufor do przechowywania danych i faktycznie wpływa na ilość danych zwracanych przez sterownik ODBC. `RFX_Text` i `RFX_Binary` tylko wykonują jedno wywołanie przy użyciu `SQLFetch` do pobierania danych z bazy danych zaplecza. Każdego sterownika ODBC ma inną ograniczenie na ilość danych, które zwracają w jednym pobierania. Ten limit może być znacznie mniejszy niż wartość w polu nMaxLength, w tym przypadku wyjątek **AFX_SQL_ERROR_DATA_TRUNCATED** zostanie zgłoszony. W tych okolicznościach, przełącz się do korzystania z `RFX_LongBinary` zamiast `RFX_Text` lub `RFX_Binary` , dzięki czemu można pobrać wszystkich danych.

Powiąż ClassWizard **SQL_LONGVARCHAR** do `CString`, lub **SQL_LONGVARBINARY** do `CByteArray` dla Ciebie. Jeśli chcesz przydzielić więcej niż 255 bajtów, na które możesz pobrać kolumny danych long, możesz podać wartość dla nMaxLength.

Gdy kolumn długich danych jest powiązany z `CString` lub `CByteArray`, aktualizowanie pola działa w taki sam jak kiedy jest on powiązany z SQL_**VARCHAR** lub SQL_**VARBINARY**. Podczas `Edit`, wartości danych są buforowane, natychmiast i później, po porównaniu `Update` jest wywoływana w celu wykrywania zmian danych, wartości i ustaw Dirty i odpowiednio Null wartości dla kolumny.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Powiązanie kolumn danych Long CLongBinary

Jeśli kolumna długich danych może zawierać więcej **MAXINT** bajtów danych, prawdopodobnie warto go do pobierania `CLongBinary`.

Zalety:

To pobranie kolumną całego długo dane do dostępnej pamięci.

Wady:

Dane są przechowywane w pamięci. To podejście jest również zbyt duży dla bardzo dużych ilości danych. Należy wywołać `SetFieldDirty` do powiązanych danych elementu członkowskiego, aby zapewnić pole znajduje się w `Update` operacji.

Po pobraniu danych long kolumny `CLongBinary`, klas baz danych będzie sprawdzić łączny rozmiar kolumny długich danych, a następnie przydzielić `HGLOBAL` segmencie pamięci jest wystarczająco duży, aby go danych całej zawierającą wartość parametru. Klasy bazy danych następnie pobrać wartości danych całej do przydzielony `HGLOBAL`.

Jeśli źródło danych nie można zwrócić oczekiwanego rozmiaru kolumny danych long, struktura spowoduje zgłoszenie wyjątku **AFX_SQL_ERROR_SQL_NO_TOTAL**. Jeśli próba przydzielić `HGLOBAL` zakończy się niepowodzeniem, standardowa pamięci wyjątku.

Powiąż ClassWizard **SQL_LONGVARCHAR** lub **SQL_LONGVARBINARY** do `CLongBinary` dla Ciebie. Wybierz `CLongBinary` jako typ zmiennej w oknie dialogowym Dodawanie zmiennej składowej. Następnie doda ClassWizard `RFX_LongBinary` wywołanie usługi `DoFieldExchange` wywołania i zwiększ całkowitą liczbę powiązanych pól.

Aby zaktualizować długo wartości kolumny danych, najpierw upewnij się, przydzielony `HGLOBAL` jest wystarczająco duży, aby pomieścić nowych danych przez wywołanie metody **:: Funkcja GlobalSize** na *m_hData* członkiem `CLongBinary`. Jeśli jest za mały, zwolnij `HGLOBAL` i przydzielić jedną odpowiedniego rozmiaru. Następnie ustaw *m_dwDataLength* celu odzwierciedlenia nowego rozmiaru.

W przeciwnym razie, jeśli *m_dwDataLength* jest większy niż rozmiar danych jest zamieniany można bezpłatnie i ponowne przydzielenie `HGLOBAL`, lub nie podawaj żadnej przydzielone. Upewnij się wskazać liczbę bajtów, które faktycznie używana w *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Jak zaktualizować działa CLongBinary

Nie jest konieczne zrozumieć, jak aktualizowanie `CLongBinary` działa, ale może być przydatne na przykład dotyczące wysyłania danych długich wartości ze źródłem danych, jeśli wybierzesz to trzecia metoda opisane poniżej.

> [!NOTE]
>  Aby `CLongBinary` pola, które mają zostać uwzględnione w aktualizacji, należy jawnie wywołać `SetFieldDirty` dla pola. W przypadku wprowadzenia zmiany pola, łącznie z ustawieniem dla niego wartość Null, należy wywołać `SetFieldDirty`. Musisz również wywołać `SetFieldNull`, za pomocą drugiego parametru jest **FALSE**, aby zaznaczyć pole jako posiadające wartość.

Podczas aktualizowania `CLongBinary` pola klasy bazy danych używanie ODBC firmy **DATA_AT_EXEC** mechanizm (zobacz dokumentację ODBC `SQLSetPos`przez rgbValue argument). Kiedy struktura przygotowuje instrukcji insert nebo update, a nie wskazuje `HGLOBAL` zawierające dane, *adres* z `CLongBinary` jest ustawiony jako *wartość* kolumny Zamiast tego i ustaw wskaźnik długość **SQL_DATA_AT_EXEC**. Później, gdy instrukcja update jest wysyłane do źródła danych, `SQLExecDirect` zwróci **SQL_NEED_DATA**. Alerty programu framework, wartości parametrów dla tej kolumny jest faktycznie adres `CLongBinary`. Struktura wywołuje `SQLGetData` raz przy użyciu małych buforów, oczekiwano sterownik zwracać rzeczywista długość danych. Jeśli sterownik zwraca rzeczywistą długością duży obiekt binarny (BLOB), MFC przydzieli tyle miejsca, co jest niezbędne do pobrania obiektu BLOB. Jeśli źródło danych zwraca **SQL_NO_TOTAL**, wskazujący, że nie może ustalić rozmiar obiektu BLOB, MFC, utworzy mniejsze bloki. Początkowy rozmiar domyślny to 64 KB, a kolejne bloki będą podwoi rozmiaru; na przykład drugi będzie 128K, trzeci to 256 KB i tak dalej. Początkowy rozmiar jest konfigurowany.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Powiązanie nie: Pobieranie/przesyłania danych bezpośrednio z ODBC z Procedura SQLGetData

Przy użyciu tej metody należy całkowicie pominąć klas baz danych i postępowania z kolumną danych long.

Zalety:

Może buforować dane na dysku, jeśli to konieczne, lub wykonać dynamicznie ilości danych do pobrania.

Wady:

Nie uzyskasz struktury `Edit` lub `AddNew` pomocy technicznej, a trzeba napisać kod, aby wykonywać podstawowe funkcje (`Delete` działa, ponieważ nie jest to operacja poziomu kolumna).

W tym przypadku kolumna długo dane muszą być na liście wyboru zestawu rekordów, ale nie może być powiązany z przez platformę. Jednym ze sposobów, aby zrobić to dostarczyć własną instrukcję SQL za pomocą `GetDefaultSQL` lub jako lpszSQL argument `CRecordset`firmy `Open` funkcji i dodatkowa kolumna za pomocą wywołania funkcji RFX_ nie tworzy wiązania. ODBC wymaga, że niepowiązanych pola są wyświetlane z prawej strony pola powiązane, dlatego dodać swoje niepowiązanych kolumn lub kolumny do końca listy wyboru.

> [!NOTE]
>  Ponieważ kolumny długich danych nie jest powiązany przez platformę, zmiany do niego nie będzie obsługiwana za pomocą `CRecordset::Update` wywołania. Należy utworzyć i wysłać SQL wymagane **Wstaw** i **aktualizacji** instrukcji samodzielnie.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

