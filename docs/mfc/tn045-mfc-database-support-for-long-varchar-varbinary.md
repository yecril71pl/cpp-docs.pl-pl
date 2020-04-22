---
title: 'TN045: obsługa bazy danych-MFC pod względem typu danych Varchar-Varbinary'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 55a68ba970d0a26163f426d51818c701c13ed051
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750278"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: obsługa MFC/bazy danych pod względem typu danych Varchar/Varbinary

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano sposób pobierania i wysyłania **SQL_LONGVARCHAR odbc** i **SQL_LONGVARBINARY** typów danych przy użyciu klas bazy danych MFC.

## <a name="overview-of-long-varcharvarbinary-support"></a>Przegląd wsparcia Long Varchar/Varbinary

Odbc **SQL_LONG_VARCHAR** i **SQL_LONGBINARY** typów danych (określanych tutaj jako długie kolumny danych) może zawierać ogromne ilości danych. Istnieją 3 sposoby obsługi tych danych:

- Powiąż `CString` / `CByteArray`go z .

- Powiąż `CLongBinary`go z .

- Nie należy wiązać go w ogóle i pobrać i wysłać długą wartość danych ręcznie, niezależnie od klas bazy danych.

Każda z trzech metod ma zalety i wady.

Długie kolumny danych nie są obsługiwane dla parametrów kwerendy. Są one obsługiwane tylko dla outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Powiązanie długiej kolumny danych z CString/CByteArray

Zalety:

Takie podejście jest proste do zrozumienia i pracujesz ze znanymi klasami. Ramy zapewniają `CFormView` wsparcie `CString` `DDX_Text`dla . Masz wiele ogólnych funkcji ciągu lub `CString` kolekcji z i `CByteArray` klas i można kontrolować ilość pamięci przydzielonej lokalnie do przechowywania wartości danych. Struktura przechowuje starą kopię danych `Edit` `AddNew` pola podczas lub wywołania funkcji, a struktura może automatycznie wykryć zmiany danych dla Ciebie.

> [!NOTE]
> Ponieważ `CString` jest przeznaczony do pracy `CByteArray` nad danymi znakowymi i do pracy nad danymi binarnymi, `CString`zaleca się umieszczenie danych znakowych (**SQL_LONGVARCHAR**) w , a dane binarne (**SQL_LONGVARBINARY**) w `CByteArray`.

Funkcje RFX `CString` `CByteArray` dla i mają dodatkowy argument, który pozwala zastąpić domyślny rozmiar przydzielonej pamięci do przechowywania pobranej wartości dla kolumny danych. Zwróć uwagę na argument nMaxLength w następujących deklaracjach funkcji:

```cpp
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

Jeśli pobierasz długą kolumnę `CString` danych `CByteArray`do lub , maksymalna zwracana ilość danych jest domyślnie 255 bajtów. Wszystko poza tym jest ignorowane. W takim przypadku struktura zda wyjątek **AFX_SQL_ERROR_DATA_TRUNCATED**. Na szczęście, można wyraźnie zwiększyć nMaxLength do większych wartości, do **MAXINT**.

> [!NOTE]
> Wartość nMaxLength jest używana przez MFC do ustawienia `SQLBindColumn` buforu lokalnego funkcji. Jest to bufor lokalny do przechowywania danych i faktycznie nie wpływa na ilość danych zwracanych przez sterownik ODBC. `RFX_Text`i `RFX_Binary` wykonać tylko `SQLFetch` jedno wywołanie przy użyciu do pobierania danych z bazy danych zaplecza. Każdy sterownik ODBC ma inne ograniczenie ilości danych, które mogą zwrócić w jednym pobraniu. Ten limit może być znacznie mniejszy niż wartość ustawiona w nMaxLength, w którym to przypadku zostanie zgłoszony wyjątek **AFX_SQL_ERROR_DATA_TRUNCATED.** W tych okolicznościach przełącz się `RFX_Text` `RFX_Binary` na używanie `RFX_LongBinary` zamiast lub tak, aby można było pobrać wszystkie dane.

ClassWizard powiąże **SQL_LONGVARCHAR** z `CString`SQL_LONGVARBINARY lub **SQL_LONGVARBINARY** `CByteArray` dla Ciebie. Jeśli chcesz przydzielić więcej niż 255 bajtów, do których można pobrać długą kolumnę danych, możesz następnie podać jawną wartość dla nMaxLength.

Gdy długa kolumna danych `CString` jest `CByteArray`powiązana z lub , aktualizowanie pola działa tak samo, jak wtedy, gdy jest powiązany z SQL_**VARCHAR** lub SQL_**VARBINARY**. Podczas `Edit`, wartość danych jest buforowane, `Update` a później porównywane, gdy jest wywoływana do wykrywania zmian wartości danych i ustawić wartości dirty i null dla kolumny odpowiednio.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Powiązanie długiej kolumny danych z CLongBinary

Jeśli długa kolumna danych może zawierać więcej bajtów **MAXINT** danych, `CLongBinary`prawdopodobnie należy rozważyć pobranie ich do pliku .

Zalety:

Spowoduje to pobranie całej długiej kolumny danych, aż do dostępnej pamięci.

Wady:

Dane są przechowywane w pamięci. Takie podejście jest również zbyt drogie w przypadku bardzo dużych ilości danych. Należy wywołać `SetFieldDirty` element członkowski danych powiązanych, aby `Update` upewnić się, że pole jest uwzględnione w operacji.

Jeśli pobierzesz długie kolumny `CLongBinary`danych do programu , klasy bazy danych sprawdzą całkowity `HGLOBAL` rozmiar długiej kolumny danych, a następnie przydzielą segment pamięci wystarczająco duży, aby pomieścić całą wartość danych. Klasy bazy danych następnie pobrać całą wartość `HGLOBAL`danych do przydzielonego .

Jeśli źródło danych nie może zwrócić oczekiwanego rozmiaru długiej kolumny danych, struktura zda wyjątek **AFX_SQL_ERROR_SQL_NO_TOTAL**. Jeśli próba przydzielenia `HGLOBAL` kończy się niepowodzeniem, zgłaszany jest wyjątek pamięci standardowej.

ClassWizard powiąże **SQL_LONGVARCHAR** lub **SQL_LONGVARBINARY** `CLongBinary` z dla Ciebie. Wybierz `CLongBinary` jako typ zmiennej w oknie dialogowym Dodawanie zmiennej elementu członkowskiego. ClassWizard następnie doda `RFX_LongBinary` wywołanie `DoFieldExchange` do połączenia i zwiększy całkowitą liczbę powiązanych pól.

Aby zaktualizować wartości długich kolumn danych, najpierw upewnij `HGLOBAL` się, że przydzielone jest wystarczająco duże, aby pomieścić nowe dane, wywołując **::GlobalSize** na *m_hData* członkiem . `CLongBinary` Jeśli jest zbyt mały, `HGLOBAL` zwolnij i przydziel odpowiedni rozmiar. Następnie ustaw *m_dwDataLength,* aby odzwierciedlić nowy rozmiar.

W przeciwnym razie, jeśli *m_dwDataLength* jest większy niż rozmiar zastępowane dane, można zwolnić i `HGLOBAL`ponownie przydzielić program , lub pozostawić je przydzielone. Pamiętaj, aby wskazać liczbę bajtów faktycznie używanych w *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Jak działa aktualizacja CLongBinary

Nie jest konieczne, aby zrozumieć, jak aktualizowanie `CLongBinary` działa, ale może być przydatne jako przykład na temat wysyłania długich wartości danych do źródła danych, jeśli wybierzesz tę trzecią metodę, opisaną poniżej.

> [!NOTE]
> Aby `CLongBinary` pole było uwzględnione w aktualizacji, należy jawnie `SetFieldDirty` wywołać to pole. Jeśli w polu zostanie dokonana jakakolwiek zmiana, w `SetFieldDirty`tym ustawienie wartości Null, należy wywołać . Należy również `SetFieldNull`wywołać , z drugim parametrem **jest FALSE**, aby oznaczyć pole jako posiadające wartość.

Podczas aktualizowania `CLongBinary` pola klasy bazy danych używają mechanizmu **DATA_AT_EXEC** ODBC (zobacz `SQLSetPos`dokumentację ODBC w argudze rgbValue firmy. Gdy struktura przygotowuje wstawianie lub aktualizowanie instrukcji, `HGLOBAL` zamiast wskazywać zawierające dane, `CLongBinary` *adres* jest ustawiany jako *wartość* kolumny, a wskaźnik długości ustawiony na **SQL_DATA_AT_EXEC**. Później, gdy instrukcja aktualizacji jest wysyłana do źródła danych, `SQLExecDirect` zwróci **SQL_NEED_DATA**. To ostrzega framework, że wartość param dla tej kolumny jest `CLongBinary`rzeczywiście adres . Ramach wywołuje `SQLGetData` raz z małym buforem, oczekując, że sterownik do zwrócenia rzeczywistej długości danych. Jeśli sterownik zwraca rzeczywistą długość binarnego dużego obiektu (BLOB), MFC ponownie przydziela tyle miejsca, ile jest to konieczne do pobrania obiektu BLOB. Jeśli źródło danych zwraca **SQL_NO_TOTAL**, wskazując, że nie można określić rozmiar obiektu BLOB, MFC utworzy mniejsze bloki. Domyślny rozmiar początkowy to 64K, a kolejne bloki będą dwukrotnie większe; na przykład drugi będzie 128K, trzeci to 256K i tak dalej. Rozmiar początkowy można konfigurować.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Niewiążące: pobieranie/wysyłanie danych bezpośrednio z odbc z SQLGetData

Za pomocą tej metody można całkowicie pominąć klas bazy danych i radzić sobie z długiej kolumny danych samodzielnie.

Zalety:

W razie potrzeby można buforować dane na dysku lub dynamicznie decydować, ile danych ma być pobieranych.

Wady:

Nie otrzymasz struktury `Edit` lub `AddNew` pomocy technicznej i należy napisać kod samodzielnie,`Delete` aby wykonać podstawowe funkcje ( działa jednak, ponieważ nie jest to operacja na poziomie kolumny).

W takim przypadku długa kolumna danych musi znajdować się na liście wyboru zestawie rekordów, ale nie powinna być powiązana przez strukturę. Jednym ze sposobów, aby to zrobić `GetDefaultSQL` jest dostarczenie własnej instrukcji SQL `CRecordset`za `Open` pośrednictwem lub jako argument lpszSQL do funkcji 's, a nie powiązać dodatkową kolumnę z wywołaniem funkcji RFX_. ODBC wymaga, aby pola niezwiązane były wyświetlane po prawej stronie pól powiązanych, więc dodaj niezwiązane kolumny lub kolumny na końcu listy wyboru.

> [!NOTE]
> Ponieważ kolumna długich danych nie jest związana z platformą, `CRecordset::Update` zmiany w niej nie będą obsługiwane za pomocą wywołań. Należy samodzielnie utworzyć i wysłać wymagane instrukcje SQL **INSERT** i **UPDATE.**

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
